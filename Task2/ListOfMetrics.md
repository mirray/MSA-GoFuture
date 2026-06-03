Since we use orchestrator - it will be responsible for most of our metrics:
1. Percentage of successfully completed rides - if increases - is looks like something goes wrong
2. Percentage of unsuccessful rides (by each unsuccessful status) - increase of average level of unsuccessful rides can lead to fail in one of microservices
3. 95 percentile of Avg. Time from request a ride to found a driver - if significantly increase  - should check geo and tracking services
4. 95 percentile of Avg. Time of payment completion - in case of banking api falls