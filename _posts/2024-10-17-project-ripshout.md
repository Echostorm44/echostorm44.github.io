---
layout: post
title: "Ripshout: Download Shoutcast Radio While You Listen"
categories:
  - Projects
tags:
  - ripshout
  - wpf
  - csharp
last_modified_at: 2025-10-17T14:25:52-05:00
---

Page to talk about Ripshout

## Deetz Here

```csharp
public static void UpdateCheckSource(string sourceID, bool isAlerted)
	{
		var cachedItem = Program.CheckSources.SingleOrDefault(a => a.SourceID == sourceID);
		if(cachedItem != null)
		{
			cachedItem.LastSeen = DateTime.UtcNow;
			cachedItem.HasAlerts = isAlerted;
			cachedItem.LastHeartbeatExpireUTC = DateTime.UtcNow.AddSeconds(cachedItem.HeartbeatSeconds);
			UpdateHeartbeatChecks();
			CheckSourcesUpdated?.Invoke();
		}
		else
		{
			PopulateCheckSourceCache();
		}
	}
 ```
