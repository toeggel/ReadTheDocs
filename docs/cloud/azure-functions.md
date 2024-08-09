---
tags:
  - Azure
  - Cloud
---

Azure Functions aka Az functions

# Notes

- Azure functions getting migrated to *isolated worker model*. Do not use *in-process* anymore.
- Isolated worker model uses a default logging filter to only log warnings and higher log-levels via `ILogger`. This filter can be disabled (see: [Azure function - Start-up and configuration](https://learn.microsoft.com/en-us/azure/azure-functions/dotnet-isolated-process-guide?tabs=windows#start-up-and-configuration)
- Logging config can be done in `host.json` for the functions host process or in `application.json` for the worker process.
- Timer based trigger uses **NCrontab** expressions (instead of normal cron expression) which uses 6 instead of 5 values (including seconds). This site can help defining cron timers: https://ncrontab.swimburger.net
- Local Az function testing / running
	- Ensure that `local.settings.json` exists (this does usually not get checked in by default) (see below). 
	- An **azure storage** is needed. Simplest solution is to use Docker for it. Otherwise an emulator will do. See: https://learn.microsoft.com/en-us/azure/storage/common/storage-use-azurite
	- `RunOnStartup` - use this to immediately trigger the function. This can also be placed in a "Debug only" block (see below).

```json
{ //  example: local.settings.json
	"IsEncrypted": false,
	"Values": {
		"AzureWebJobsStorage": "UseDevelopmentStorage=true",
		"FUNCTIONS_WORKER_RUNTIME": "dotnet-isolated"
}  
```

```csharp
// example for RunOnStartup only in debug
public async Task Run(
	[TimerTrigger("0 15/30 9-20 * 5-9 *"
#if DEBUG
	, RunOnStartup=true
#endif
	)] TimerInfo myTimer)
```