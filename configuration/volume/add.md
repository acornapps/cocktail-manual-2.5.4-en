### 5.4.1 Add Storage

---

This feature allows you to add storage volumes.

##### **a\) Cluster → Select Cluster.**![](/assets/EN/2.5/5.4.1_1.png)

##### b**\) Select a volume from the detailed cluster screen**![](/assets/EN/2.5/5.4.1_2.png)

##### c\) Enter cluster, name, description, storage plugin, Reclaim Policy, and storage class name in order.![](/assets/EN/2.5/5.4.1_3.png)

| **Storage Info** | **Description** |
| :--- | :--- |
| Name | PV name |
| Description | User-defined PV description |
| Storage Plugin | Type of storage \(NFS Dynamic/Static, EBS, Google Persistent Disk, Azure Disk\) |
| Reclaim Policy | PV usage policy \(RETAIN/DELETE\) |
| Storage Class Name | Class name registered in k8s |
| Parameters | PV environment settings |

| **Policy** | **Description** |
| :--- | :--- |
| Retain | The data in a persistent volume \(PV\) remains even if the persistent volume claim \(PVC\) is deleted. Although it can be reused, the PV must be re-registered |
| Delete | When a PVC is deleted, the corresponding PV is also deleted |

##### 

##### d\) Set the storage class and parameters according to the storage plugin being used.

* ##### If using NFS dynamic storage plugin![](/assets/EN/2.5/5.4.1_4.png)

| Storage Plugin | **NFS** Dynamic |
| :--- | :--- |
| Policy | The dynamic plugin supports the Retain and Delete policies |
| Storage Class Name | cocktail-nfs \(Default value\) |

* **If using NFS static storage plugin**![](/assets/EN/2.5/5.4.1_5.png)

| Storage Plugin | **NFS** Static |
| :--- | :--- |
| Policy | The static plugin only supports the Retain policy |
| Parameter | Server: IP address of storage. Path: Mount path |

* **If using AWS storage plugin**![](/assets/EN/2.5/5.4.1_6.png)

| Storage Plugin | AWS EBS \(AWS storage service\) |
| :--- | :--- |
| Storage Class Name | default \(Fixed value\) |

* **If using Google storage plugin**![](/assets/EN/2.5/5.4.1_7.png)

| Storage Plugin | Google Persistent Disk \(GCP storage service\) |
| :--- | :--- |
| Storage Class Name | standard\(Default value\) |

* **If using Azure storage plugin**![](/assets/EN/2.5/5.4.1_8.png)

| Storage Plugin | Azure Disk \(Azure storage service\) |
| :--- | :--- |
| Storage Class Name | default\(Default value\) |



