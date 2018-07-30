#
# 5.5.1 Alert List

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
| Action | The [ETCD metric document](https://github.com/coreos/etcd/blob/master/Documentation/metrics.md/) says that <br /> ETCD cluster downtime is getting longer due to temporary electoral failure or lack of members. <br /> Check if there is a reader or an abandoned ETCD member |

| Alarm ID | **ETC-012** |
| :--- | :--- |
| Severity | warning |
| Alarm Name | HighFsyncDurations |
| duration | 10minute |
| occurrence condition | 최근 5분 동안의 wal fsync 지속 시간의 99번째 백분위가 500ms보다 클 경우<br /> \(wal fsync: 로그 항목을 적용하기 전에 디스크에 저장시 호출.\) |
| Action | [ETCD 메트릭 문서](https://github.com/coreos/etcd/blob/master/Documentation/metrics.md) 따르면 디스크에 문제가 있을 경우 발생한다고 함. |

| Alarm ID | **ETC-013** |
| :--- | :--- |
| Severity | warning |
| Alarm Name | HighCommitDurations |
| duration | 10minute |
| occurrence condition | 최근 5분 동안의 커밋 지속 시간 중 99번째 백분위가 250ms보다 클 경우<br /> \(backend commit: 디스크에 대한 최근 변경 사항의 증분 스냅 샷의 커밋.\) |
| Action | [ETCD 메트릭 문서](https://github.com/coreos/etcd/blob/master/Documentation/metrics.md%29에) 따르면 디스크에 문제가 있을 경우 발생한다고 함. |

* #### General

| Alarm ID | **GEN-001** |
| :--- | :--- |
| Severity | warning |
| Alarm Name | TargetDown |
| duration | 10minute |
| occurrence condition | 메트릭 수집 작업이 안 될 경우 발생. 어떤 작업이 실패인지 표시됨. |
| Action | Prometheus의 로그 및 해당 작업에 해당하는 Pod의 로그 및 이벤트를 확인한다. |

| Alarm ID | **GEN-002** |
| :--- | :--- |
| Severity | ~~none~~ |
| Alarm Name | DeadMansSwitch |
| duration | Immediately |
| occurrence condition | DeadMansSwitch 알림. |
| Action | 해당 알람은 사용자에게 통지되지 않습니다. |

| Alarm ID | **GEN-003** |
| :--- | :--- |
| Severity | **critical** |
| Alarm Name | TooManyOpenFileDescriptors |
| duration | 10minute |
| occurrence condition | file descriptor 사용율이 95%이상 일때 발생 |
| Action | 노드의 Limit값을 변경한다.\(노드의 재시작 필요\) |

| Alarm ID | **GEN-004** |
| :--- | :--- |
| Severity | warning |
| Alarm Name | FdExhaustionClose |
| duration | 10minute |
| occurrence condition | 단순회귀분석\(simple linear regression\)을 이용하여 4시간 이내에<br /> file descriptor 고갈이 예측될 경우 발생 |
| Action | 해당 Pod의 로그 및 이벤트를 확인한다.<br /> 필요할 경우, 노드의 Limit값을 변경한다.\(노드의 재시작 필요\) |

| Alarm ID | **GEN-005** |
| :--- | :--- |
| Severity | **critical** |
| Alarm Name | FdExhaustionClose |
| duration | 10minute |
| occurrence condition | 단순회귀분석\(simple linear regression\)을 이용하여 1시간 이내에<br /> file descriptor 고갈이 예측될 경우 발생 |
| Action | 해당 Pod의 로그 및 이벤트를 확인한다.<br /> 필요할 경우, 노드의 Limit값을 변경한다.\(노드의 재시작 필요\) |

* #### Kube-ApiServer

| Alarm ID | **KAS-001** |
| :--- | :--- |
| Severity | **critical** |
| Alarm Name | K8SApiserverDown |
| duration | 5minute |
| occurrence condition | kube-apiserver 메트릭 수집이 안 될 경우 발생 |
| Action | Prometheus의 로그 및 kube-apiserver의 로그와 이벤트를 확인한다.<br /> 필요할 경우, Pod를 재시작한다. |

| Alarm ID | **KAS-002** |
| :--- | :--- |
| Severity | warning |
| Alarm Name | K8SApiServerLatency |
| duration | 10minute |
| occurrence condition | 최근 10분 동안의 요청 대기 시간 중 99번째 백분위가 1s보다 클 경우 발생 |
| Action | 계속 발생할 경우, 마스터 노드를 증설한다. |

* #### Kube-ControllerManager

| Alarm ID | **KCM-001** |
| :--- | :--- |
| Severity | **critical** |
| Alarm Name | K8SControllerManagerDown |
| duration | 5minute |
| occurrence condition | kube-controller-manager 메트릭 수집이 안 될 경우 발생 |
| Action | Prometheus의 로그 및 kube-controller-manager의 로그와 이벤트를 확인한다.<br /> 필요할 경우, Pod를 재시작한다. |

* #### Kube-Scheduler

| Alarm ID | **KSC-001** |
| :--- | :--- |
| Severity | **critical** |
| Alarm Name | K8SSchedulerDown |
| duration | 5minute |
| occurrence condition | kube-scheduler 메트릭 수집이 안 될 경우 발생 |
| Action | Prometheus의 로그 및 kube-scheduler의 로그와 이벤트를 확인한다.<br /> 필요할 경우, Pod를 재시작한다. |

* #### Kube-State-Metrics

| Alarm ID | **KSM-001** |
| :--- | :--- |
| Severity | warning |
| Alarm Name | DeploymentGenerationMismatch |
| duration | 15minute |
| occurrence condition | Deployment에 설정한 generation과 수집된 generation이 다를 경우 발생 |
| Action | Deployment의 로그 및 이벤트를 확인한다.<br /> 필요하면 Deployment를 재배포한다. |

| Alarm ID | **KSM-002** |
| :--- | :--- |
| Severity | warning |
| Alarm Name | DeploymentReplicasNotUpdated |
| duration | 15minute |
| occurrence condition | Deployment에 설정한 replica 개수와 변경되거나 available 상태의<br /> replica 개수가 다를 경우 발생 |
| Action | Deployment 수정 사항이 반영이 안 된 상태이므로 Deployment 및<br /> Pod의 로그 및 이벤트를 확인한다. |

| Alarm ID | **KSM-003** |
| :--- | :--- |
| Severity | warning |
| Alarm Name | DaemonSetRolloutStuck |
| duration | 15minute |
| occurrence condition | DaemonSet에 상태가 Ready가 아닌 Pod가 있을 경우 발생 |
| Action | 해당 Daemonset과 Pod의 로그 및 이벤트를 확인한다. |

| Alarm ID | **KSM-004** |
| :--- | :--- |
| Severity | warning |
| Alarm Name | K8SDaemonSetsNotScheduled |
| duration | 10minute |
| occurrence condition | DaemonSet에 실행되어 할 Pod 개수 보다 실행중인<br /> Pod 개수가 작을 경우 발생 |
| Action | 해당 Daemonset과 Pod의 로그 및 이벤트를 확인한다.<br /> 배포가 안 된 노드가 정상인지 확인한다.<br /> 마스터 노드가 격리된 경우, Daemonset에 toleration 설정이 되어 있는지 확인한다. |

| Alarm ID | **KSM-005** |
| :--- | :--- |
| Severity | warning |
| Alarm Name | DaemonSetsMissScheduled |
| duration | 10minute |
| occurrence condition | DaemonSet에 잘못 스케쥴된 Pod가 생겼을 경우 발생 |
| Action | 해당 Daemonset과 Pod의 로그 및 이벤트를 확인한다. |

| Alarm ID | **KSM-006** |
| :--- | :--- |
| Severity | warning |
| Alarm Name | PodFrequentlyRestarting |
| duration | 10minute |
| occurrence condition | 최근 1시간 동안 Pod 재시작 횟수가 5회 이상일 경우 발생 |
| Action | 해당 Pod의 로그 및 이벤트를 확인한다. 필요하면 Pod를 재시작한다. |

* #### Kubelet

| Alarm ID | **KBL-001** |
| :--- | :--- |
| Severity | warning |
| Alarm Name | K8SNodeNotReady |
| duration | 1hours |
| occurrence condition | Node 상태가 Ready가 아닐 경우 발생 |
| Action | 해당 노드의 상태 및 이벤트를 확인한다.<br /> ssh를 통해 노드에 접속하여 kubelet의 상태를 확인한다. |

| Alarm ID | **KBL-002** |
| :--- | :--- |
| Severity | **critical** |
| Alarm Name | K8SManyNodesNotReady |
| duration | 1minute |
| occurrence condition | 클러스터 전체에서 Node 상태가 Ready가 아닌 비율이 20%이상일 경우 발생 |
| Action | 해당 노드들의 상태 및 이벤트를 확인한다.<br /> ssh를 통해 노드에 접속하여 kubelet의 상태를 확인한다. |

| Alarm ID | **KBL-003** |
| :--- | :--- |
| Severity | warning |
| Alarm Name | K8SKubeletDown |
| duration | 1hours |
| occurrence condition | 클러스터 전체에서 3%이상의 kubelet 메트릭 수집이 안 될 경우 발생 |
| Action | Prometheus의 로그 및 해당 노드의 상태 및 이벤트를 확인한다.<br /> ssh를 통해 노드에 접속하여 kubelet의 상태를 확인한다. |

| Alarm ID | **KBL-004** |
| :--- | :--- |
| Severity | **critical** |
| Alarm Name | K8SKubeletDown |
| duration | 1hours |
| occurrence condition | 클러스터 전체에서 10%이상의 kubelet 메트릭 수집이 안 될 경우 발생 |
| Action | Prometheus의 로그 및 해당 노드들의 상태 및 이벤트를 확인한다.<br /> ssh를 통해 노드에 접속하여 kubelet의 상태를 확인한다. |

| Alarm ID | **KBL-005** |
| :--- | :--- |
| Severity | warning |
| Alarm Name | K8SKubeletTooManyPods |
| duration | Immediately |
| occurrence condition | Node의 배치된 Pod의 수가 100개가 넘으면 발생.\(제한값은 110\) |
| Action | 제한값에 도달할 경우, 더 이상 Pod 생성이 안됨.<br /> 다른 노드들의 상태도 같이 확인하여 여유가 없을 경우, 노드를 증설한다. |

* #### Node

| Alarm ID | **NOD-001** |
| :--- | :--- |
| Severity | warning |
| Alarm Name | NodeExporterDown |
| duration | 10minute |
| occurrence condition | NodeExporter 메트릭 수집이 안 될 경우 발생 |
| Action | Prometheus의 로그 및 NodeExporter의 로그와 이벤트를 확인한다.<br /> 필요할 경우, Pod를 재시작한다. |

| Alarm ID | **NOD-002** |
| :--- | :--- |
| Severity | **critical** |
| Alarm Name | K8SNodeOutOfDisk |
| duration | Immediately |
| occurrence condition | Node 상태가 OutOfDisk일 때 발생 |
| Action | 해당 노드의 디스크를 증설한다. |

| Alarm ID | **NOD-003** |
| :--- | :--- |
| Severity | warning |
| Alarm Name | K8SNodeMemoryPressure |
| duration | Immediately |
| occurrence condition | Node 상태가 MemoryPressure일 때 발생 |
| Action | 해당 노드의 메모리를 증설한다. |

| Alarm ID | **NOD-004** |
| :--- | :--- |
| Severity | warning |
| Alarm Name | K8SNodeDiskPressure |
| duration | Immediately |
| occurrence condition | Node 상태가 DiskPressure일 때 발생 |
| Action | 노드에서 로그, 미사용 dodkcer image, pv backup등을 삭제하여 디스크 공간을 확보한다.<br /> 계속 발생할 경우, 해당 노드의 디스크를 증설한다. |

| Alarm ID | **NOD-005** |
| :--- | :--- |
| Severity | warning |
| Alarm Name | NodeCPUUsage |
| duration | 30minute |
| occurrence condition | Node 최근 5분간 평균 CPU 사용량이 90%를 넘을 경우 발생 |
| Action | 해당 노드의 CPU를 증설한다. |

| Alarm ID | **NOD-006** |
| :--- | :--- |
| Severity | warning |
| Alarm Name | NodeMemoryUsage |
| duration | 30minute |
| occurrence condition | Node Memory 사용량이 90%를 넘을 경우 발생 |
| Action | 해당 노드의 메모리를 증설한다. |

* #### Prometheus

| Alarm ID | **PRM-001** |
| :--- | :--- |
| Severity | warning |
| Alarm Name | PrometheusFailedReload |
| duration | 10minute |
| occurrence condition | Prometheus의 설정 변경시, 설정 다시읽기 작업 실패시 발생 |
| Action | 해당 Pod의 로그를 확인하여 ConfigMap의 설정 오류를 수정한다. |

* #### Cocktail

| Alarm ID | **CKT-001** |
| :--- | :--- |
| Severity | warning |
| Alarm Name | PvLowRequestDisk |
| duration | 30minute |
| occurrence condition | PV가 요청한 디스크의 크기 대비 사용량이 80%가 넘으면 발생 |
| Action | PV의 크기를 늘린다. 단, 서버를 재배포 해야함. |

| Alarm ID | **CKT-002** |
| :--- | :--- |
| Severity | warning |
| Alarm Name | PvLowTotalDisk |
| duration | 30minute |
| occurrence condition | PV가 마운트된 디스크의 크기 대비 사용량이 80%가 넘으면 발생 |
| Action | 마운트된 디스크의 상태를 확인하고 미사용 PV를 제거한다.<br /> 필요하면 디스크를 증설한다. |

| Alarm ID | **CKT-003** |
| :--- | :--- |
| Severity | warning |
| Alarm Name | PodCPULimitUsage |
| duration | 30minute |
| occurrence condition | Resource Limit 설정값 대비 CPU 사용율이 90%가 넘으면 발생 |
| Action | 계속 발생할 경우, Deployment의 CPU Limit 값 변경 |

| Alarm ID | **CKT-004** |
| :--- | :--- |
| Severity | warning |
| Alarm Name | PodMemoryLimitUsage |
| duration | 30minute |
| occurrence condition | Resource Limit 설정값 대비 Memory 사용율이 90%가 넘으면 발생 |
| Action | 계속 발생할 경우, Deployment의 Memory Limit 값 변경 |



