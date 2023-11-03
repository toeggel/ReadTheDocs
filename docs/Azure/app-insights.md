# AppInsights

AppInsights uses the SQL like KQL (Kusto Query Language). Microsoft has a nice SQL to KQL cheat sheet: https://learn.microsoft.com/en-us/azure/data-explorer/kusto/query/sqlcheatsheet

## Example Snippets

Some examples that helped me in the past.

```sql
// counts of a unique sessions who saw the "login-failed" page
pageViews 
| where name contains "login-failed"
| summarize failed_page_viewed = sum(itemCount) by session_Id
```

```sql
// everything we find for a sepcific session where the severity is > 1
union *
| where session_Id == "RHiMNyqmN77t2WWCiAxdvf"
| where severityLevel > 1
| order by timestamp desc 
```

```sql
// A timechart of how often the "login-failed" page was viewed per day
pageViews 
| where name contains "login-failed"
| summarize count() by bin(timestamp, 1d) 
| order by timestamp desc 
| render timechart  
```

```sql
// Read everything where the session_Id matches a session_Id who visited the "login-failed" page
union *
| where session_Id in (toscalar(
    pageViews
    | where name contains "login-failed"
    | summarize makeset(session_Id)
    ))
| order by timestamp desc 
```

```sql
// Failed request grouped by HttpStatusCode displayed with columns per day
requests
| where success == false
| summarize count() by resultCode, bin(timestamp, 1d) 
| order by timestamp desc 
| render columnchart  
```  