## 5.5.1 Alerts List

---

An alert occurs when the occurrence condition in the following list continues for the duration time.

* #### AlertManager

| Alarm ID | **ALM-001** |
| :--- | :--- |
| Severity | warning |
| Alarm Name | AlertmanagerDown |
| duration | 5minute |
| occurrence condition | Alertmanager Occurs when metrics can not be collected |
| Action | Check Prometheus logs and Alertmanager logs and events. If necessary, restart the Pod. |

| Alarm ID | **ALM-002** |
| :--- | :--- |
| Severity | warning |
| Alarm Name | AlertmanagerFailedReload |
| duration | 10minute |
| occurrence condition | When setting change of Alertmanager, it occurs when setting re-read operation fails |
| Action | Check the log of the pod to fix the configuration error of ConfigMap. |

* #### ETCD3

| Alarm ID | **ETC-001** |
| :--- | :--- |
| Severity | **critical** |
| Alarm Name | InsufficientMembers |
| duration | 3minute |
| occurrence condition | Occurs when ETCD metrics can not be collected |
| Action | Check the status of the ETCD cluster. Check Prometheus's log and its node's etc status. |

| Alarm ID | **ETC-002** |
| :--- | :--- |
| Severity | **critical** |
| Alarm Name | NoLeader |
| duration | 1minute |
| occurrence condition | Occurs when there is no ETCD reader |
| Action | Check the status of the ETCD cluster. Disk Latency may be a problem, so run the following command on all nodes of the ETCD cluster. \([ETCD Tuning](https://coreos.com/etcd/docs/latest/tuning.html#disk)\)<br /> ``$ sudo ionice -c2 -n0 -p `pgrep etcd` `` |

| Alarm ID | **ETC-003** |
| :--- | :--- |
| Severity | warning |
| Alarm Name | HighNumberOfLeaderChanges |
| duration | Immediately |
| occurrence condition | If there are more than 3 reader changes in the last hour |
| Action | Check the status of the ETCD cluster. Disk Latency may be a problem, so run the following command on all nodes of the ETCD cluster. \([ETCD Tuning](https://coreos.com/etcd/docs/latest/tuning.html#disk)\)<br /> ``$ sudo ionice -c2 -n0 -p `pgrep etcd` `` |

| Alarm ID | **ETC-004** |
| :--- | :--- |
| Severity | warning |
| Alarm Name | HighNumberOfFailedGRPCRequests |
| duration | 10minute |
| occurrence condition | If more than 1% of gRPC method calls fail within the last 5 minutes |
| Action | Increase the bandwidth of ETCD clusters and Kubernetes clusters, or Sacale-Up clusters. |

| Alarm ID | **ETC-005** |
| :--- | :--- |
| Severity | **critical** |
| Alarm Name | HighNumberOfFailedGRPCRequests |
| duration | 5minute |
| occurrence condition | If more than 5% of gRPC method calls fail within the last 5 minutes |
| Action | Increase the bandwidth of ETCD clusters and Kubernetes clusters, or Sacale-Up clusters. |

| Alarm ID | **ETC-006** |
| :--- | :--- |
| Severity | **critical** |
| Alarm Name | GRPCRequestsSlow |
| duration | 10minute |
| occurrence condition | If the 99th percentile of the gRPC method request latency over the last 5 minutes is greater than 150ms |
| Action | Increase the bandwidth of ETCD clusters and Kubernetes clusters, or Sacale-Up clusters. |

| Alarm ID | **ETC-007** |
| :--- | :--- |
| Severity | warning |
| Alarm Name | HighNumberOfFailedHTTPRequests |
| duration | 10minute |
| occurrence condition | If more than 1% of requests for HTTP endpoints fail within the last 5 minutes |
| Action | Increase the bandwidth of ETCD clusters and Kubernetes clusters, or Sacale-Up clusters. |

| Alarm ID | **ETC-008** |
| :--- | :--- |
| Severity | **critical** |
| Alarm Name | HighNumberOfFailedHTTPRequests |
| duration | 5minute |
| occurrence condition | If more than 5% of requests for HTTP endpoints fail within the last 5 minutes |
| Action | Increase the bandwidth of ETCD clusters and Kubernetes clusters, or Sacale-Up clusters. |

| Alarm ID | **ETC-009** |
| :--- | :--- |
| Severity | warning |
| Alarm Name | HTTPRequestsSlow |
| duration | 10minute |
| occurrence condition | If the 99th percentile of the HTTP request latency during the last 5 minutes is greater than 150ms |
| Action | Increase the bandwidth of ETCD clusters and Kubernetes clusters, or Sacale-Up clusters. |

| Alarm ID | **ETC-010** |
| :--- | :--- |
| Severity | warning |
| Alarm Name | EtcdMemberCommunicationSlow |
| duration | 10minute |
| occurrence condition | If the 99th percentile of the communication wait time between members in the last 5 minutes is greater than 150ms |
| Action | ETCD Increase the bandwidth of the cluster or scale up the cluster. |

| Alarm ID | **ETC-011** |
| :--- | :--- |
| Severity | warning |
| Alarm Name | HighNumberOfFailedProposals |
| duration | Immediately |
| occurrence condition | If there are more than 5 failed raft protocol requests in the last hour. <br /> \(RAFT Protocol is ETCD Synchronization Protocol \). |
| Action | The [ETCD metric document](https://github.com/coreos/etcd/blob/master/Documentation/metrics.md/) says that ETCD cluster downtime is getting longer due to temporary electoral failure or lack of members. Check if there is a reader or an abandoned ETCD member |

| Alarm ID | **ETC-012** |
| :--- | :--- |
| Severity | warning |
| Alarm Name | HighFsyncDurations |
| duration | 10minute |
| occurrence condition | If the 99th percentile of the wal fsync duration for the last 5 minutes is greater than 500ms (wal fsync: Called when saving to disk before applying log entries.) |
| Action | According to the [ETCD metrics document](https://github.com/coreos/etcd/blob/master/Documentation/metrics.md/), there is a problem with the disk. |

| Alarm ID | **ETC-013** |
| :--- | :--- |
| Severity | warning |
| Alarm Name | HighCommitDurations |
| duration | 10minute |
| occurrence condition | If the 99th percentile of the last 5 minutes is greater than 250ms, then backend commit is the incremental snapshot commit of the most recent change to the disk. |
| Action | According to the [ETCD metrics document](https://github.com/coreos/etcd/blob/master/Documentation/metrics.md/), there is a problem with the disk. |

* #### General

| Alarm ID | **GEN-001** |
| :--- | :--- |
| Severity | warning |
| Alarm Name | TargetDown |
| duration | 10minute |
| occurrence condition | Occurs when metric gathering is not possible. Indicates which operation failed. |
| Action | Check the Prometheus log and the logs and events of the pod corresponding to the job. |

| Alarm ID | **GEN-002** |
| :--- | :--- |
| Severity | ~~none~~ |
| Alarm Name | DeadMansSwitch |
| duration | Immediately |
| occurrence condition | DeadMansSwitch notification. |
| Action | The alarm is not notified to the user. |

| Alarm ID | **GEN-003** |
| :--- | :--- |
| Severity | **critical** |
| Alarm Name | TooManyOpenFileDescriptors |
| duration | 10minute |
| occurrence condition | Occurs when file descriptor usage is over 95% |
| Action | Change the limit value of the node. (Requires restart of node) |

| Alarm ID | **GEN-004** |
| :--- | :--- |
| Severity | warning |
| Alarm Name | FdExhaustionClose |
| duration | 10minute |
| occurrence condition | If the file descriptor depletion is predicted within 4 hours using simple linear regression |
| Action | Check the logs and events of the corresponding pod. If necessary, change the limit value of the node. (Requires restart of node) |

| Alarm ID | **GEN-005** |
| :--- | :--- |
| Severity | **critical** |
| Alarm Name | FdExhaustionClose |
| duration | 10minute |
| occurrence condition | If the file descriptor depletion is predicted within 1 hours using simple linear regression |
| Action | Check the logs and events of the corresponding pod. If necessary, change the limit value of the node. (Requires restart of node) |

* #### Kube-ApiServer

| Alarm ID | **KAS-001** |
| :--- | :--- |
| Severity | **critical** |
| Alarm Name | K8SApiserverDown |
| duration | 5minute |
| occurrence condition | kube-apiserver Occurs when metrics can not be collected |
| Action | Check Prometheus logs and kube-apiserver logs and events. If necessary, restart the Pod. |

| Alarm ID | **KAS-002** |
| :--- | :--- |
| Severity | warning |
| Alarm Name | K8SApiServerLatency |
| duration | 10minute |
| occurrence condition | If the 99th percentile of the waiting time for the last 10 minutes is greater than 1s |
| Action | If it continues to occur, the master node is added. |

* #### Kube-ControllerManager

| Alarm ID | **KCM-001** |
| :--- | :--- |
| Severity | **critical** |
| Alarm Name | K8SControllerManagerDown |
| duration | 5minute |
| occurrence condition | kube-controller-manager Occurs when metrics can not be collected |
| Action | Check Prometheus logs and kube-controller-manager logs and events. If necessary, restart the Pod. |

* #### Kube-Scheduler

| Alarm ID | **KSC-001** |
| :--- | :--- |
| Severity | **critical** |
| Alarm Name | K8SSchedulerDown |
| duration | 5minute |
| occurrence condition | If kube-scheduler metrics can not be collected |
| Action | Check Prometheus logs and kube-scheduler logs and events. If necessary, restart the Pod. |

* #### Kube-State-Metrics

| Alarm ID | **KSM-001** |
| :--- | :--- |
| Severity | warning |
| Alarm Name | DeploymentGenerationMismatch |
| duration | 15minute |
| occurrence condition | Occurs when generation set in Deployment differs from collected generation |
| Action | Check the logs and events of the deployment. If necessary, redistribute Deployment. |

| Alarm ID | **KSM-002** |
| :--- | :--- |
| Severity | warning |
| Alarm Name | DeploymentReplicasNotUpdated |
| duration | 15minute |
| occurrence condition | Occurs when the number of replicas set in the deployment is different from the number of replicas in the changed or available state. |
| Action | Check the logs and events of Deployment and Pod because Deployment fix is not reflected. |

| Alarm ID | **KSM-003** |
| :--- | :--- |
| Severity | warning |
| Alarm Name | DaemonSetRolloutStuck |
| duration | 15minute |
| occurrence condition | Occurs when there are pods whose status is not Ready in DaemonSet |
| Action | Check the Daemonset and Pod logs and events. |

| Alarm ID | **KSM-004** |
| :--- | :--- |
| Severity | warning |
| Alarm Name | K8SDaemonSetsNotScheduled |
| duration | 10minute |
| occurrence condition | Occurs when the number of running pods is smaller than the number of pods to be executed in DaemonSet. |
| Action | Check the Daemonset and Pod logs and events. Verify that the node that is not deployed is healthy. If the master node is isolated, make sure that the daemonset has tolerance settings. |

| Alarm ID | **KSM-005** |
| :--- | :--- |
| Severity | warning |
| Alarm Name | DaemonSetsMissScheduled |
| duration | 10minute |
| occurrence condition | Occurs when an improperly scheduled pod is encountered in DaemonSet |
| Action | Check the Daemonset and Pod logs and events. |

| Alarm ID | **KSM-006** |
| :--- | :--- |
| Severity | warning |
| Alarm Name | PodFrequentlyRestarting |
| duration | 10minute |
| occurrence condition | Occurs when the number of pod restarts is more than 5 times in the last hour |
| Action | Check the logs and events of the corresponding pod. Restart the Pod if necessary. |

* #### Kubelet

| Alarm ID | **KBL-001** |
| :--- | :--- |
| Severity | warning |
| Alarm Name | K8SNodeNotReady |
| duration | 1hours |
| occurrence condition | Occurs when the Node state is not Ready |
| Action | Check the status and events of that node. Connect to the node via ssh and check the status of the kubelet. |

| Alarm ID | **KBL-002** |
| :--- | :--- |
| Severity | **critical** |
| Alarm Name | K8SManyNodesNotReady |
| duration | 1minute |
| occurrence condition | Occurs when the percentage of nodes that are not Ready is more than 20% across the cluster |
| Action | Check the status and events of the nodes. Connect to the node via ssh and check the status of the kubelet. |

| Alarm ID | **KBL-003** |
| :--- | :--- |
| Severity | warning |
| Alarm Name | K8SKubeletDown |
| duration | 1hours |
| occurrence condition | Occurs when kubelet metrics are not collected over 3% across the cluster |
| Action | Check the Prometheus log and its node status and events. Connect to the node via ssh and check the status of the kubelet. |

| Alarm ID | **KBL-004** |
| :--- | :--- |
| Severity | **critical** |
| Alarm Name | K8SKubeletDown |
| duration | 1hours |
| occurrence condition | Occurs when more than 10% kubelet metrics are not collected across the cluster |
| Action | Check the Prometheus logs and their status and events. Connect to the node via ssh and check the status of the kubelet. |

| Alarm ID | **KBL-005** |
| :--- | :--- |
| Severity | warning |
| Alarm Name | K8SKubeletTooManyPods |
| duration | Immediately |
| occurrence condition | Occurs when the number of pods placed in the Node exceeds 100 (the limit is 110) |
| Action | If the limit value is reached, no more pod generation is possible. If the state of other nodes is checked as well, the node is added. |

* #### Node

| Alarm ID | **NOD-001** |
| :--- | :--- |
| Severity | warning |
| Alarm Name | NodeExporterDown |
| duration | 10minute |
| occurrence condition | NodeExporter occurs when metrics can not be collected |
| Action | Check the Prometheus logs and NodeExporter logs and events. If necessary, restart the Pod. |

| Alarm ID | **NOD-002** |
| :--- | :--- |
| Severity | **critical** |
| Alarm Name | K8SNodeOutOfDisk |
| duration | Immediately |
| occurrence condition | Occurs when the Node state is OutOfDisk. |
| Action | The disk of the node is expanded. |

| Alarm ID | **NOD-003** |
| :--- | :--- |
| Severity | warning |
| Alarm Name | K8SNodeMemoryPressure |
| duration | Immediately |
| occurrence condition | Occurs when the Node state is MemoryPressure |
| Action | The memory of the node is expanded. |

| Alarm ID | **NOD-004** |
| :--- | :--- |
| Severity | warning |
| Alarm Name | K8SNodeDiskPressure |
| duration | Immediately |
| occurrence condition | Occurs when Node Status is DiskPressure |
| Action | Free up disk space by removing logs, unused dodkcer image, and pv backup from the node. If it continues to occur, the disk of the corresponding node is added. |

| Alarm ID | **NOD-005** |
| :--- | :--- |
| Severity | warning |
| Alarm Name | NodeCPUUsage |
| duration | 30minute |
| occurrence condition | Node Average CPU usage in the last 5 minutes exceeds 90% |
| Action | Increase the CPU of the node. |

| Alarm ID | **NOD-006** |
| :--- | :--- |
| Severity | warning |
| Alarm Name | NodeMemoryUsage |
| duration | 30minute |
| occurrence condition | Node memory usage exceeds 90% |
| Action | The memory of the node is expanded. |

* #### Prometheus

| Alarm ID | **PRM-001** |
| :--- | :--- |
| Severity | warning |
| Alarm Name | PrometheusFailedReload |
| duration | 10minute |
| occurrence condition | Prometheus changes settings, re-read settings |
| Action | Check the log of the pod to fix the configuration error of ConfigMap. |

* #### Cocktail

| Alarm ID | **CKT-001** |
| :--- | :--- |
| Severity | warning |
| Alarm Name | PvLowRequestDisk |
| duration | 30minute |
| occurrence condition | PV is over 80% of the requested disk size |
| Action | Increase the size of PV. However, you must redistribute the server. |

| Alarm ID | **CKT-002** |
| :--- | :--- |
| Severity | warning |
| Alarm Name | PvLowTotalDisk |
| duration | 30minute |
| occurrence condition | Occurs when PV is mounted on a disk and its usage exceeds 80%. |
| Action | Check the status of the mounted disk and remove unused PV. If necessary, expand the disk. |

| Alarm ID | **CKT-003** |
| :--- | :--- |
| Severity | warning |
| Alarm Name | PodCPULimitUsage |
| duration | 30minute |
| occurrence condition | Occurs when the CPU utilization exceeds 90% of the Resource Limit setting value |
| Action | Change the CPU Limit value of the Deployment if it continues to occur |

| Alarm ID | **CKT-004** |
| :--- | :--- |
| Severity | warning |
| Alarm Name | PodMemoryLimitUsage |
| duration | 30minute |
| occurrence condition | Occurs when memory usage exceeds 90% of Resource Limit setting value |
| Action | Change Memory Limit value of Deployment if it continues to occur |



