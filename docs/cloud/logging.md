---
tags:
  - Azure
  - Logging
  - KQL
  - SPL
---

# App Insights

AppInsights uses the SQL like KQL (Kusto Query Language). Microsoft has a nice SQL to KQL cheat sheet: https://learn.microsoft.com/en-us/azure/data-explorer/kusto/query/sqlcheatsheet

## Example Snippets

Some examples that helped me in the past.

```kusto
// counts of a unique sessions who saw the "login-failed" page
pageViews 
| where name contains "login-failed"
| summarize failed_page_viewed = sum(itemCount) by session_Id
```

```kusto
// everything we find for a sepcific session where the severity is > 1
union *
| where session_Id == "RHiMNyqmN77t2WWCiAxdvf"
| where severityLevel > 1
| order by timestamp desc 
```

```kusto
// A timechart of how often the "login-failed" page was viewed per day
pageViews 
| where name contains "login-failed"
| summarize count() by bin(timestamp, 1d) 
| order by timestamp desc 
| render timechart  
```

```kusto
// Read everything where the session_Id matches a session_Id who visited the "login-failed" page
union *
| where session_Id in (toscalar(
    pageViews
    | where name contains "login-failed"
    | summarize makeset(session_Id)
    ))
| order by timestamp desc 
```

```kusto
// Failed request grouped by HttpStatusCode displayed with columns per day
requests
| where success == false
| summarize count() by resultCode, bin(timestamp, 1d) 
| order by timestamp desc 
| render columnchart  
```  

# Splunk

Splunk uses SPL ((Splunk) search processing language) which is similar to KQL. 

## Example Snippets

use triple escape for quotes:
```splunk-spl
\\\"sustainabilityProfile\\\":\\\"NOT_RELEVANT\\\"
```

```splunk-spl
// extract a json value based on it's key, select only non-empty values and display a unique list of found values
app=SomeApp
| rex field Message "\"someJsonKey\": \"(?<myValue>.*)\","
| search myValue!=""
| stats values(myValue) as unique_myValues
```

https://google.com