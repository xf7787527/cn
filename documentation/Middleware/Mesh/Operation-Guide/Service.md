# 服务

## 概述

服务发现是将特定的业务服务加入到网格中，是可对服务进行治理和观测的先决条件。MESH 支持自动发现 K8S 集群中的服务和手工注册其他类型的服务如 VM、云数据库等。

## 自动发现

网格中默认会展示k8s集群内的服务。

## 手动注册

借助 Istio 的 Service Entry、Workload Entry 机制，可以在 MESH中添加非 托管K8S集群中的服务，例如传统的 VM 服务、数据库服务等。Service Entry 对应 K8S 中的 Service 概念，某个服务通过 Service Entry 加入网格后，将可被网格内其他自动发现的服务按照路由规则访问。Workload Entry 对应 K8S 中 Workload 概念，用于标记一组与 Service Entry 对应的服务实体程序，安装 Sidecar 后的 workload Entry 可与其他自动发现的 K8S workload 一样，实现流量控制、安全增强、服务观测等能力。

### Service Entry 重要字段说明

| 字段名称            | 字段格式   | 字段说明                                                                                                                                                                       |
| --------------- | ------ | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| spec.hosts      | string | 服务的 URL 中的 hostname，可以有多个。                                                                                                                                                 |
| spec.ports      | Port[] | 服务端口号，可以有多个。                                                                                                                                                               |
| spec.resolution | string | <li>Static：使用静态的 endpoint ip 地址作为服务实例。<br/><li>DNS：通过 DNS 解析服务 endpoint ip 地址，多用于外部服务；申明的 endpoint 需使用 DNS 域名，在无 endpoint 情况下将解析服务为 hosts 域名。<br/><li>NONE：当服务无需 IP 解析时选择。 |
| spec.location   | string | 用于标记此服务是否在网格内，部分 Istio 能力特性不能在网格外服务使用，例如网格外的服务不支持mTLS。MESH_EXTERNAL 代表网格外的服务，MESH_INTERNAL 代表网格内服务。                                                                        |
| spec.endpoints  | String | 服务的接入点，可填写多个，但最终只会同时使用一个。                                                                                                                                                  |

### Workload Entry 重要字段说明

| 字段名称                | 字段格式   | 字段说明                                            |
| ------------------- | ------ | ----------------------------------------------- |
| spec.address        | string | 当前 endpoint 的地址，类似于 pod IP。                     |
| spec.labels         | string | 当前 endpoint 的标签，用于与 Service Entry 关联。           |
| sepc.serviceAccount | string | sidecar 的权限信息，当需要为 endpoint 添加 sidecar 的时候需要指定。 |

关于 Service Entry、Workload Entry 的详细介绍，请参见 [Service Entry 详细介绍](https://istio.io/latest/docs/reference/config/networking/service-entry/)，[Workload Entry详细介绍](https://istio.io/latest/docs/reference/config/networking/workload-entry/)。
