---
title: Review events and errors using Event Viewer
description: Get descriptions and further troubleshooting steps (if required) for all events reported by the Microsoft Defender for Endpoint service.
keywords: troubleshoot, event viewer, log summary, failure code, failed, Microsoft Defender for Endpoint service, cannot start, broken, can't start
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.date: 05/21/2018
ms.technology: mde
---


# Review events and errors using Event Viewer

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Applies to:**
- Event Viewer
- [Microsoft Defender for Endpoint](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

>Want to experience Microsoft Defender for Endpoint? [Sign up for a free trial.](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-enablesiem-abovefoldlink)

You can review event IDs in the [Event Viewer](https://msdn.microsoft.com/library/aa745633(v=bts.10).aspx) on individual devices.

For example, if devices are not appearing in the **Devices list**, you might need to look for event IDs on the devices. You can then use this table to determine further troubleshooting steps.

**Open Event Viewer and find the Microsoft Defender for Endpoint service event log:**

1. Click **Start** on the Windows menu, type **Event Viewer**, and press **Enter**.

2. In the log list, under **Log Summary**, scroll until you see **Microsoft-Windows-SENSE/Operational**. Double-click the item to
   open the log.

   a.  You can also access the log by expanding **Applications and Services Logs** > **Microsoft** > **Windows** > **SENSE** and click on **Operational**.

   > [!NOTE]
   > SENSE is the internal name used to refer to the behavioral sensor that powers Microsoft Defender for Endpoint.

3. Events recorded by the service will appear in the log. See the following table for a list of events recorded by the service.

<table>
<tbody style="vertical-align:top;">
<tr>
<th>Event ID</th>
<th>Message</th>
<th>Description</th>
<th>Action</th>
</tr>
<tr>
<td>1</td>
<td>Microsoft Defender for Endpoint service started (Version <code>variable</code>).</td>
<td>Occurs during system start up, shut down, and during onbboarding.</td>
<td>Normal operating notification; no action required.</td>
</tr>
<tr>
<td>2</td>
<td>Microsoft Defender for Endpoint service shutdown.</td>
<td>Occurs when the device is shut down or offboarded.</td>
<td>Normal operating notification; no action required.</td>
</tr>
<tr>
<td>3</td>
<td>Microsoft Defender for Endpoint service failed to start. Failure code: <code>variable</code>.</td>
<td>Service did not start.</td>
<td>Review other messages to determine possible cause and troubleshooting steps.</td>
</tr>
<tr>
<td>4</td>
<td>Microsoft Defender for Endpoint service contacted the server at <code>variable</code>.</td>
<td>Variable = URL of the Defender for Endpoint processing servers.<br>
This URL will match that seen in the Firewall or network activity.</td>
<td>Normal operating notification; no action required.</td>
</tr>
<tr>
<td>5</td>
<td>Microsoft Defender for Endpoint service failed to connect to the server at <code>variable</code>.</td>
<td>Variable = URL of the Defender for Endpoint processing servers.<br>
The service could not contact the external processing servers at that URL.</td>
<td>Check the connection to the URL. See <a href="configure-proxy-internet.md" data-raw-source="[Configure proxy and Internet connectivity](configure-proxy-internet.md)">Configure proxy and Internet connectivity</a>.</td>
</tr>
<tr>
<td>6</td>
<td>Microsoft Defender for Endpoint service is not onboarded and no onboarding parameters were found.</td>
<td>The device did not onboard correctly and will not be reporting to the portal.</td>
<td>Onboarding must be run before starting the service.<br>
Check that the onboarding settings and scripts were deployed properly. Try to redeploy the configuration packages.<br>
See <a href="configure-endpoints.md" data-raw-source="[Onboard Windows 10 devices](configure-endpoints.md)">Onboard Windows 10 devices</a>.</td>
</tr>
<tr>
<td>7</td>
<td>Microsoft Defender for Endpoint service failed to read the onboarding parameters. Failure: <code>variable</code>.</td>
<td>Variable = detailed error description. The device did not onboard correctly and will not be reporting to the portal.</td>
<td>Check that the onboarding settings and scripts were deployed properly. Try to redeploy the configuration packages.<br>
See <a href="configure-endpoints.md" data-raw-source="[Onboard Windows 10 devices](configure-endpoints.md)">Onboard Windows 10 devices</a>.</td>
</tr>
<tr>
<td>8</td>
<td>Microsoft Defender for Endpoint service failed to clean its configuration. Failure code: <code>variable</code>.</td>
<td><b>During onboarding:</b> The service failed to clean its configuration during the onboarding. The onboarding process continues. <br><br> <b>During offboarding:</b> The service failed to clean its configuration during the offboarding. The offboarding process finished but the service keeps running.
 </td>
<td><b>Onboarding:</b> No action required. <br><br> <b>Offboarding:</b> Reboot the system.<br>
See <a href="configure-endpoints.md" data-raw-source="[Onboard Windows 10 devices](configure-endpoints.md)">Onboard Windows 10 devices</a>.</td>
</tr>
<tr>
<td>9</td>
<td>Microsoft Defender for Endpoint service failed to change its start type. Failure code: <code>variable</code>.</td>
<td><b>During onboarding:</b> The device did not onboard correctly and will not be reporting to the portal. <br><br><b>During offboarding:</b> Failed to change the service start type. The offboarding process continues. </td>
<td>Check that the onboarding settings and scripts were deployed properly. Try to redeploy the configuration packages.<br>
See <a href="configure-endpoints.md" data-raw-source="[Onboard Windows 10 devices](configure-endpoints.md)">Onboard Windows 10 devices</a>.</td>
</tr>
<tr>
<td>10</td>
<td>Microsoft Defender for Endpoint service failed to persist the onboarding information. Failure code: <code>variable</code>.</td>
<td>The device did not onboard correctly and will not be reporting to the portal.</td>
<td>Check that the onboarding settings and scripts were deployed properly. Try to redeploy the configuration packages.<br>
See <a href="configure-endpoints.md" data-raw-source="[Onboard Windows 10 devices](configure-endpoints.md)">Onboard Windows 10 devices</a>.</td>
</tr>
<tr>
<td>11</td>
<td>Onboarding or re-onboarding of Defender for Endpoint service completed.</td>
<td>The device onboarded correctly.</td>
<td>Normal operating notification; no action required.<br>
It may take several hours for the device to appear in the portal.</td>
</tr>
<tr>
<td>12</td>
<td>Microsoft Defender for Endpoint failed to apply the default configuration.</td>
<td>Service was unable to apply the default configuration.</td>
<td>This error should resolve after a short period of time.</td>
</tr>
<tr>
<td>13</td>
<td>Microsoft Defender for Endpoint device ID calculated: <code>variable</code>.</td>
<td>Normal operating process.</td>
<td>Normal operating notification; no action required.</td>
</tr>
<tr>
<td>15</td>
<td>Microsoft Defender for Endpoint cannot start command channel with URL: <code>variable</code>.</td>
<td>Variable = URL of the Defender for Endpoint processing servers.<br>
The service could not contact the external processing servers at that URL.</td>
<td>Check the connection to the URL. See <a href="configure-proxy-internet.md" data-raw-source="[Configure proxy and Internet connectivity](configure-proxy-internet.md)">Configure proxy and Internet connectivity</a>.</td>
</tr>
<tr>
<td>17</td>
<td>Microsoft Defender for Endpoint service failed to change the Connected User Experiences and Telemetry service location. Failure code: <code>variable</code>.</td>
<td>An error occurred with the Windows telemetry service.</td>
<td><a href="troubleshoot-onboarding.md#ensure-that-microsoft-defender-antivirus-is-not-disabled-by-a-policy" data-raw-source="[Ensure the diagnostic data service is enabled](troubleshoot-onboarding.md#ensure-that-microsoft-defender-antivirus-is-not-disabled-by-a-policy)">Ensure the diagnostic data service is enabled</a>.<br>
Check that the onboarding settings and scripts were deployed properly. Try to redeploy the configuration packages.<br>
See <a href="configure-endpoints.md" data-raw-source="[Onboard Windows 10 devices](configure-endpoints.md)">Onboard Windows 10 devices</a>.</td>
</tr>
<tr>
<td>18</td>
<td>OOBE (Windows Welcome) is completed.</td>
<td>Service will only start after any Windows updates have finished installing.</td>
<td>Normal operating notification; no action required.</td>
</tr>
<tr>
<td>19</td>
<td>OOBE (Windows Welcome) has not yet completed.</td>
<td>Service will only start after any Windows updates have finished installing.</td>
<td>Normal operating notification; no action required.<br>
If this error persists after a system restart, ensure all Windows updates have full installed.</td>
</tr>
<tr>
<td>20</td>
<td>Cannot wait for OOBE (Windows Welcome) to complete. Failure code: <code>variable</code>.</td>
<td>Internal error.</td>
<td>If this error persists after a system restart, ensure all Windows updates have full installed.</td>
</tr>
<tr>
<td>25</td>
<td>Microsoft Defender for Endpoint service failed to reset health status in the registry. Failure code: <code>variable</code>.</td>
<td>The device did not onboard correctly.
It will report to the portal, however the service may not appear as registered in SCCM or the registry.</td>
<td>Check that the onboarding settings and scripts were deployed properly. Try to redeploy the configuration packages.<br>
See <a href="configure-endpoints.md" data-raw-source="[Onboard Windows 10 devices](configure-endpoints.md)">Onboard Windows 10 devices</a>.</td>
</tr>
<tr>
<td>26</td>
<td>Microsoft Defender for Endpoint service failed to set the onboarding status in the registry. Failure code: <code>variable</code>.</td>
<td>The device did not onboard correctly.<br>
It will report to the portal, however the service may not appear as registered in SCCM or the registry.</td>
<td>Check that the onboarding settings and scripts were deployed properly. Try to redeploy the configuration packages.<br>
See <a href="configure-endpoints.md" data-raw-source="[Onboard Windows 10 devices](configure-endpoints.md)">Onboard Windows 10 devices</a>.</td>
</tr>
<tr>
<td>27</td>
<td>Microsoft Defender for Endpoint service failed to enable SENSE aware mode in Microsoft Defender Antivirus. Onboarding process failed. Failure code: <code>variable</code>.</td>
<td>Normally, Microsoft Defender Antivirus will enter a special passive state if another real-time antimalware product is running properly on the device, and the device is reporting to Defender for Endpoint.</td>
<td>Check that the onboarding settings and scripts were deployed properly. Try to redeploy the configuration packages.<br>
See <a href="configure-endpoints.md" data-raw-source="[Onboard Windows 10 devices](configure-endpoints.md)">Onboard Windows 10 devices</a>.<br>
Ensure real-time antimalware protection is running properly.</td>
</tr>
<tr>
<td>28</td>
<td>Microsoft Defender for Endpoint Connected User Experiences and Telemetry service registration failed. Failure code: <code>variable</code>.</td>
<td>An error occurred with the Windows telemetry service.</td>
<td><a href="troubleshoot-onboarding.md#ensure-that-microsoft-defender-antivirus-is-not-disabled-by-a-policy" data-raw-source="[Ensure the diagnostic data service is enabled](troubleshoot-onboarding.md#ensure-that-microsoft-defender-antivirus-is-not-disabled-by-a-policy)">Ensure the diagnostic data service is enabled</a>.<br>
Check that the onboarding settings and scripts were deployed properly. Try to redeploy the configuration packages.<br>
See <a href="configure-endpoints.md" data-raw-source="[Onboard Windows 10 devices](configure-endpoints.md)">Onboard Windows 10 devices</a>.</td>
</tr>
<tr>
<td>29</td>
<td>Failed to read the offboarding parameters. Error type: %1, Error code: %2, Description: %3 </td>
<td>This event occurs when the system can&#39;t read the offboarding parameters.</td>
<td>Ensure the device has Internet access, then run the entire offboarding process again. Ensure the offboarding package has not expired.</td>
</tr>
<tr>
<td>30</td>
<td>Microsoft Defender for Endpoint service failed to disable SENSE aware mode in Microsoft Defender Antivirus. Failure code: <code>variable</code>.</td>
<td>Normally, Microsoft Defender Antivirus will enter a special passive state if another real-time antimalware product is running properly on the device, and the device is reporting to Defender for Endpoint.</td>
<td>Check that the onboarding settings and scripts were deployed properly. Try to redeploy the configuration packages.<br>
See <a href="configure-endpoints.md" data-raw-source="[Onboard Windows 10 devices](configure-endpoints.md)">Onboard Windows 10 devices</a><br>
Ensure real-time antimalware protection is running properly.</td>
</tr>
<tr>
<td>31</td>
<td>Microsoft Defender for Endpoint Connected User Experiences and Telemetry service unregistration failed. Failure code: <code>variable</code>.</td>
<td>An error occurred with the Windows telemetry service during onboarding. The offboarding process continues.</td>
<td><a href="troubleshoot-onboarding.md#ensure-the-diagnostic-data-service-is-enabled" data-raw-source="[Check for errors with the Windows telemetry service](troubleshoot-onboarding.md#ensure-the-diagnostic-data-service-is-enabled)">Check for errors with the Windows telemetry service</a>.</td>
</tr>
<tr>
<td>32</td>
<td>Microsoft Defender for Endpoint service failed to request to stop itself after offboarding process. Failure code: %1</td>
<td>An error occurred during offboarding.</td>
<td>Reboot the device.</td>
</tr>
<tr>
<td>33</td>
<td>Microsoft Defender for Endpoint service failed to persist SENSE GUID. Failure code: <code>variable</code>.</td>
<td>A unique identifier is used to represent each device that is reporting to the portal.<br>
If the identifier does not persist, the same device might appear twice in the portal.</td>
<td>Check registry permissions on the device to ensure the service can update the registry.</td>
</tr>
<tr>
<td>34</td>
<td>Microsoft Defender for Endpoint service failed to add itself as a dependency on the Connected User Experiences and Telemetry service, causing onboarding process to fail. Failure code: <code>variable</code>.</td>
<td>An error occurred with the Windows telemetry service.</td>
<td><a href="troubleshoot-onboarding.md#ensure-that-microsoft-defender-antivirus-is-not-disabled-by-a-policy" data-raw-source="[Ensure the diagnostic data service is enabled](troubleshoot-onboarding.md#ensure-that-microsoft-defender-antivirus-is-not-disabled-by-a-policy)">Ensure the diagnostic data service is enabled</a>.<br>
Check that the onboarding settings and scripts were deployed properly. Try to redeploy the configuration packages.<br>
See <a href="configure-endpoints.md" data-raw-source="[Onboard Windows 10 devices](configure-endpoints.md)">Onboard Windows 10 devices</a>.</td>
</tr>
<tr>
<td>35</td>
<td>Microsoft Defender for Endpoint service failed to remove itself as a dependency on the Connected User Experiences and Telemetry service. Failure code: <code>variable</code>.</td>
<td>An error occurred with the Windows telemetry service during offboarding. The offboarding process continues.
</td>
<td>Check for errors with the Windows diagnostic data service.</td>
</tr>
<tr>
<td>36</td>
<td>Microsoft Defender for Endpoint Connected User Experiences and Telemetry service registration succeeded. Completion code: <code>variable</code>.</td>
<td>Registering Defender for Endpoint with the Connected User Experiences and Telemetry service completed successfully.</td>
<td>Normal operating notification; no action required.</td>
</tr>
<tr>
<td>37</td>
<td>Microsoft Defender for Endpoint A module is about to exceed its quota. Module: %1, Quota: {%2} {%3}, Percentage of quota utilization: %4.</td>
<td>The device has almost used its allocated quota of the current 24-hour window. It’s about to be throttled.</td>
<td>Normal operating notification; no action required.</td>
</tr>
<tr>
<td>38</td>
<td>Network connection is identified as low. Microsoft Defender for Endpoint will contact the server every %1 minutes. Metered connection: %2, internet available: %3, free network available: %4.</td>
<td>The device is using a metered/paid network and will be contacting the server less frequently.</td>
<td>Normal operating notification; no action required.</td>
</tr>
<tr>
<td>39</td>
<td>Network connection is identified as normal. Microsoft Defender for Endpoint will contact the server every %1 minutes. Metered connection: %2, internet available: %3, free network available: %4.</td>
<td>The device is not using a metered/paid connection and will contact the server as usual.</td>
<td>Normal operating notification; no action required.</td>
</tr>
<tr>
<td>40</td>
<td>Battery state is identified as low. Microsoft Defender for Endpoint will contact the server every %1 minutes. Battery state: %2.</td>
<td>The device has low battery level and will contact the server less frequently.</td>
<td>Normal operating notification; no action required.</td>
</tr>
<tr>
<td>41</td>
<td>Battery state is identified as normal. Microsoft Defender for Endpoint will contact the server every %1 minutes. Battery state: %2.</td>
<td>The device doesn’t have low battery level and will contact the server as usual.</td>
<td>Normal operating notification; no action required.</td>
</tr>
<tr>
<td>42</td>
<td>Microsoft Defender for Endpoint WDATP component failed to perform action. Component: %1, Action: %2, Exception Type: %3, Exception message: %4</td>
<td>Internal error. The service failed to start.</td>
<td>If this error persists, contact Support.</td>
</tr>
<tr>
<td>43</td>
<td>Microsoft Defender for Endpoint WDATP component failed to perform action. Component: %1, Action: %2, Exception Type: %3, Exception Error: %4, Exception message: %5</td>
<td>Internal error. The service failed to start.</td>
<td>If this error persists, contact Support.</td>
</tr>
<tr>
<td>44</td>
<td>Offboarding of Defender for Endpoint service completed.</td>
<td>The service was offboarded.</td>
<td>Normal operating notification; no action required.</td>
</tr>
<tr>
<td>45</td>
<td>Failed to register and to start the event trace session [%1]. Error code: %2</td>
<td>An error occurred on service startup while creating ETW session. This caused service start-up failure.</td>
<td>If this error persists, contact Support.</td>
</tr>
<tr>
<td>46</td>
<td>Failed to register and start the event trace session [%1] due to lack of resources. Error code: %2. This is most likely because there are too many active event trace sessions. The service will retry in 1 minute.</td>
<td>An error occurred on service startup while creating ETW session due to lack of resources. The service started and is running, but will not report any sensor event until the ETW session is started.</td>
<td>Normal operating notification; no action required. The service will try to start the session every minute.</td>
</tr>
<tr>
<td>47</td>
<td>Successfully registered and started the event trace session - recovered after previous failed attempts.</td>
<td>This event follows the previous event after successfully starting of the ETW session.</td>
<td>Normal operating notification; no action required.</td>
</tr>
<tr>
<td>48</td>
<td>Failed to add a provider [%1] to event trace session [%2]. Error code: %3. This means that events from this provider will not be reported.</td>
<td>Failed to add a provider to ETW session. As a result, the provider events aren’t reported.</td>
<td>Check the error code. If the error persists contact Support.</td>
</tr>
</tr>
</tbody>
</table>

>Want to experience Microsoft Defender for Endpoint? [Sign up for a free trial.](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-eventerrorcodes-belowfoldlink)

## Related topics
- [Onboard Windows 10 devices](configure-endpoints.md)
- [Configure device proxy and Internet connectivity settings](configure-proxy-internet.md)
- [Troubleshoot Microsoft Defender for Endpoint](troubleshoot-onboarding.md)
