\# Setup Guide



\## 1. Lab Environment



| Component | Details |

|----------|----------|

| Hypervisor | VMware Workstation Pro |

| SIEM Platform | Splunk Enterprise |

| Splunk Version | 10.4.2 |

| Splunk Package | splunk-10.4.2-33c3bf42cd73-linux-amd64.deb |

| Splunk Server OS | Ubuntu 26.04 Desktop (64-bit) |

| Endpoint OS | Windows 11 |

| Forwarder | Splunk Universal Forwarder 10.4.2 |

| Endpoint Monitoring | Sysmon |

| Sysmon Configuration | SwiftOnSecurity Sysmon Configuration |



\---



\# 2. Network Configuration



| Component | Address |

|-----------|---------|

| Splunk Web | http://192.168.88.xxx:8000 |

| Splunk Receiving Port | 9997/TCP |

| Splunk Server IP | 192.168.88.xxx |

| Windows Endpoint | 192.168.88.xxx |



> \*\*Note:\*\* Private IP addresses have been partially masked for security.



\---



\# 3. Splunk Enterprise Installation



\- Installed Splunk Enterprise 10.4.2 on Ubuntu 26.04 Desktop.

\- Accepted the Splunk license.

\- Configured the administrator account.

\- Enabled Splunk to start automatically at boot.

\- Verified access through the Splunk Web interface.



\---



\# 4. Universal Forwarder Installation



Installed Splunk Universal Forwarder 10.4.2 on the Windows 11 endpoint.



Configured forwarding to the Splunk Enterprise server using TCP port \*\*9997\*\*.



Configured Windows Event Log monitoring through `inputs.conf`.



\---



\# 5. Receiving Port Configuration



Configured Splunk Enterprise as a receiving indexer.



\*\*Receiving Port\*\*



```

9997/TCP

```



Verified that the Universal Forwarder successfully established a connection with the indexer.



\---



\# 6. Index Creation



Created a dedicated index for endpoint telemetry.



| Setting | Value |

|---------|-------|

| Index Name | soc\_endpoint |

| Index Type | Events |

| Data Integrity | Enabled |

| Storage | Default |



\---



\# 7. Sysmon Installation



Installed Microsoft Sysmon on the Windows endpoint.



Applied the SwiftOnSecurity Sysmon configuration to generate detailed endpoint telemetry, including:



\- Process Creation

\- Process Termination

\- Network Connections

\- File Creation

\- Registry Activity

\- DLL Loading

\- Remote Thread Creation

\- DNS Events



Verified that Sysmon events were successfully recorded in:



```

Microsoft-Windows-Sysmon/Operational

```



\---



\# 8. Splunk Add-ons



Installed the following Splunk Add-ons on the Splunk Enterprise server.



\- Splunk Add-on for Microsoft Windows

\- Sysmon Add-on for Splunk



\---



\# 9. Log Collection



The following Windows Event Logs are forwarded to Splunk.



\- Application

\- Security

\- System

\- Microsoft-Windows-Sysmon/Operational



Telemetry is indexed into:



```

soc\_endpoint

```



\---



\# 10. Verification



Verified successful ingestion of endpoint telemetry by confirming:



\- Windows Event Logs received

\- Security Events indexed

\- System Events indexed

\- Sysmon Events indexed

\- Event searches returned expected results

\- Universal Forwarder connected successfully



Example searches used during validation:



```spl

index=soc\_endpoint

```



```spl

index=soc\_endpoint

| stats count by source

```



```spl

index=soc\_endpoint source=\*Sysmon\*

```



```spl

index=soc\_endpoint source=\*Sysmon\* EventID=1

```



\---



\# Current Status



✅ Splunk Enterprise Operational



✅ Universal Forwarder Connected



✅ Receiving Port (9997) Enabled



✅ Sysmon Installed



✅ Windows Telemetry Ingested



✅ Endpoint Events Indexed Successfully

