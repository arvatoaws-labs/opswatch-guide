Opswatch Guide
============

Introduction
----
This guide describes how the Opswatch service can be installed.

Futher product information can be found here:
https://www.arvato-systems.com/solutions-technologies/technologies/amazon-web-services/opswatch

Deploy IAM Stacks in each AWS Account
----
Use IaC tool of your choice:
* https://github.com/arvatoaws-labs/cdk-opswatch-iam
* https://github.com/arvatoaws-labs/cfn-opswatch-iam
* https://github.com/arvatoaws-labs/terraform-opswatch-iam

Deploy Metrics Stream Stack in each AWS Account and used Region
----
Use IaC tool of your choice:
* https://github.com/arvatoaws-labs/cdk-opswatch-metric-stream
* https://github.com/arvatoaws-labs/cfn-opswatch-metric-stream
* https://github.com/arvatoaws-labs/terraform-opswatch-metric-stream

Setup additional scrape config and rules for Prometheus
----
Use flux to install the rules and scrape config in Prometheus using this guide https://github.com/arvatoaws-labs/opswatch-prometheus-rules

Replace Placeholders
* CLIENT_ID_PROVIDED_BY_ARVATO = xxxxxxxx
* CLIENT_SECRET_PROVIDED_BY_ARVATO = zzzzz
* URL_PROVIDED_BY_ARVATO = https://xyz

Ensure that metrics and alerts are present
----
* Check if alarms like AwsCloudwatch* are present
* Check if metrics like aws_cloudwatch_CloudWatch_* are present
* Check if alarm AwsCloudwatchMetricUpdateRateLow does not show an error
* Check if all account ids and regions are present in this query: sum by(overwrite_asy_customer, overwrite_aws_account_id, overwrite_aws_region) (rate(aws_cloudwatch_CloudWatch_MetricUpdate_sum[15m]))
