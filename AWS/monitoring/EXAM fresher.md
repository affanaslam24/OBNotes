**Enable detailed monitoring on all EC2 instances and use Amazon CloudWatch metrics for analysis:** This is the correct solution because detailed monitoring provides metrics at 1-minute intervals, which allows the operations team to quickly detect and analyze potential bottlenecks during the sales event. CloudWatch natively supports metrics for both EC2 and RDS.

**Configure Amazon CloudWatch Logs Insights to aggregate application logs for both the EC2 instances and Amazon RDS. Use Amazon QuickSight for detailed visualization:** This is incorrect because while Logs Insights is useful for log analysis, it does not directly provide 1-minute metric granularity required for real-time monitoring.

**Configure an Amazon CloudWatch Events rule to trigger an AWS Lambda function that collects custom metrics from the EC2 instances and Amazon RDS. Use Amazon CloudWatch dashboards to display the metrics:** This is incorrect because using CloudWatch detailed monitoring is a simpler and more efficient solution compared to creating custom metrics with Lambda.

