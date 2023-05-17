Postmortem: Outage Incident on Web Stack

Issue Summary:
Duration: May 10, 2023, 14:00 WTC - May 11, 2023, 03:00 WTC
Impact: The online marketplace service experienced a complete outage during the incident. Users were unable to access the website or perform any transactions. Approximately 80% of users were affected by the outage.

Timeline:

May 10, 2023, 14:00 WTC: The issue was detected when monitoring alerts indicated a sudden drop in server response times.
May 10, 2023, 14:05 WTC: The operations team started investigating the issue, suspecting a potential database problem due to the high load.
May 10, 2023, 14:15 WTC: After analyzing the database logs, it was determined that the database was functioning normally.
May 10, 2023, 14:30 WTC: Attention was shifted towards the application layer, where engineers noticed a spike in CPU usage on one of the web servers.
May 10, 2023, 14:40 WTC: Further analysis revealed a memory leak issue in the web application code.
May 10, 2023, 15:00 WTC: The incident was escalated to the development team, responsible for the web application.
May 10, 2023, 16:00 WTC: Developers identified the root cause as an inefficient caching mechanism, leading to excessive memory consumption.
May 10, 2023, 17:00 TC: A temporary workaround was implemented to alleviate the memory leak and restore service functionality.
May 11, 2023, 02:00 WTC: The permanent fix was deployed to production.
May 11, 2023, 03:00 WTC: The service was fully restored, and users regained access to the online marketplace.
Root Cause and Resolution:
The root cause of the outage was traced back to an inefficient caching mechanism within the web application code. The caching mechanism was not properly managing memory usage, resulting in a continuous increase in memory consumption over time. As memory reached its limit, the web server experienced a significant performance degradation, ultimately leading to the complete outage.

To resolve the issue, the development team implemented a two-step approach:

Temporary Workaround: The team identified the specific code module responsible for the memory leak and implemented a temporary fix to mitigate the excessive memory consumption. This workaround involved periodically flushing the cache and optimizing the caching algorithm to reduce memory usage. This allowed the service to be partially restored.
Permanent Fix: The developers thoroughly refactored the caching mechanism, addressing the memory leak issue at its core. They implemented a more efficient memory management strategy, optimized cache eviction policies, and introduced additional monitoring to detect and handle memory-related anomalies.
Corrective and Preventative Measures:
To prevent similar incidents in the future, the following measures have been identified:

Code Review: Conduct a comprehensive review of the entire codebase, specifically focusing on caching mechanisms, to identify and address any potential memory leaks or inefficient memory usage.
Performance Testing: Implement rigorous performance testing procedures to identify and address performance bottlenecks before they impact the production environment.
Continuous Monitoring: Enhance the monitoring system to include more granular memory usage metrics and automated alerts to proactively detect abnormal memory consumption patterns.
Incident Response Plan: Review and enhance the incident response plan to ensure efficient and timely escalation of critical issues, involving the necessary teams and stakeholders.
