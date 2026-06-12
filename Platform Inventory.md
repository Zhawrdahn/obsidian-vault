| Policy               | Project      | What it checks | Threshold | Channels   | Owner    | Fires/30d | Verdict   | Notes                                            |
| -------------------- | ------------ | -------------- | --------- | ---------- | -------- | --------- | --------- | ------------------------------------------------ |
| `cpu-high-prod`      | dp-prod-core | GCE CPU util   | >90% 5m   | PagerDuty  | Platform | 142       | 🔴 Tune   | Fires on batch jobs, raise to 95% or scope label |
| `bq-slot-contention` | dp-prod-bq   | BQ slot usage  | >95% 15m  | Slack      | Data Eng | 38        | 🟡 Review | Expected during month-end                        |
| `composer-dag-fail`  | dp-prod-orch | DAG failures   | any       | Slack + PD | Platform | 12        | 🟢 Keep   |                                                  |
| `disk-low-dev`       | sandbox-7    | Disk free      | <10%      | none       | ❓        | 0         | ⚫ Delete  | No channel = pointless                           |
