# 京东云VPC


## 简介
VPC相关API，包含产品线：VPC、子网、路由表、安全组、ACL、VPC peering、弹性公网IP、共享带宽包、弹性网卡。


### 版本
v1


## API
|接口名称|请求方式|功能描述|
|---|---|---|
|**createVpc**|POST|创建私有网络|
|**deleteVpc**|DELETE|删除私有网络|
|**modifyVpc**|PATCH|修改私有网络接口|
|**describeVpcs**|GET|查询私有网络列表|
|**describeVpc**|GET|查询Vpc信息详情|
|**createSubnet**|POST|创建子网|
|**deleteSubnet**|DELETE|删除子网|
|**modifySubnet**|PATCH|修改子网接口|
|**describeSubnets**|GET|查询子网列表|
|**describeSubnet**|GET|查询子网信息详情|
|**createRouteTable**|POST|创建路由表|
|**deleteRouteTable**|DELETE|删除路由表|
|**modifyRouteTable**|PATCH|修改路由表属性|
|**associateRouteTable**|POST|路由表绑定子网接口|
|**disassociateRouteTable**|POST|给路由表解绑子网接口|
|**addRouteTableRules**|POST|添加路由表规则|
|**removeRouteTableRules**|POST|移除路由表规则|
|**modifyRouteTableRules**|POST|修改路由表规则|
|**describeRouteTables**|GET|查询路由表列表|
|**describeRouteTable**|GET|查询路由表信息详情|
|**createNetworkAcl**|POST|创建networkAcl接口|
|**deleteNetworkAcl**|DELETE|删除networkAcl接口|
|**modifyNetworkAcl**|PATCH|修改networkAcl接口|
|**associateNetworkAcl**|POST|给子网绑定networkAcl接口|
|**disassociateNetworkAcl**|POST|给子网解绑networkAcl接口|
|**addNetworkAclRules**|POST|添加networkAcl规则接口|
|**removeNetworkAclRules**|POST|移除networkAcl规则|
|**modifyNetworkAclRules**|POST|修改networkAcl接口|
|**describeNetworkAcls**|GET|查询Acl列表|
|**describeNetworkAcl**|GET|查询networkAcl资源详情|
|**assignSecondaryIps**|POST|给网卡分配secondaryIp接口|
|**associateElasticIp**|POST|给网卡绑定弹性Ip接口|
|**disassociateElasticIp**|POST|给网卡解绑弹性Ip接口|
|**unassignSecondaryIps**|POST|给网卡删除secondaryIp接口|
|**createNetworkInterface**|POST|创建网卡接口，只能创建辅助网卡|
|**deleteNetworkInterface**|DELETE|删除弹性网卡接口|
|**describeNetworkInterface**|GET|查询弹性网卡信息详情|
|**describeNetworkInterfaces**|GET|查询弹性网卡列表|
|**modifyNetworkInterface**|PATCH|修改弹性网卡接口|
|**createElasticIps**|POST|创建一个或者多个弹性公网 IP|
|**deleteElasticIp**|DELETE|删除弹性 IP|
|**modifyElasticIp**|PATCH|修改弹性 IP|
|**describeElasticIp**|GET|弹性公网IP信息详情|
|**describeElasticIps**|GET|查询弹性公网 IP 列表|
|**createBandwidthPackage**|POST|创建一个共享带宽包|
|**addBandwidthPackageIP**|DELETE|向共享带宽包中添加公网 IP|
|**describeBandwidthPackage**|GET|查询共享带宽包信息详情|
|**describeBandwidthPackage**|GET|查询共享带宽包列表|
|**deleteBandwidthPackage**|DELETE|删除共享带宽包|
|**modifyBandwidthPackage**|PATCH|修改共享带宽包|
|**modifyBandwidthPackageIpBandwidth**|POST|修改共享带宽包中公网IP的带宽上限|
|**removeBandwidthPackageIP**|POST|从共享带宽包中移除公网 IP|
|**createNetworkSecurityGroup**|POST|创建安全组|
|**deleteNetworkSecurityGroup**|DELETE|删除安全组|
|**modifyNetworkSecurityGroup**|PATCH|修改安全组属性|
|**addNetworkSecurityGroupRules**|POST|添加安全组规则|
|**removeNetworkSecurityGroupRules**|POST|移除安全组规则|
|**modifyNetworkSecurityGroupRules**|POST|修改安全组规则|
|**describeNetworkSecurityGroup**|GET|查询安全组信息详情|
|**describeNetworkSecurityGroups**|GET|查询安全组列表|
|**createVpcPeering**|POST|创建VpcPeering接口|
|**deleteVpcPeering**|DELETE|删除VpcPeering接口|
|**modifyVpcPeering**|PUT|修改VpcPeering接口|
|**describeVpcPeering**|GET|查询VpcPeering资源详情|
|**describeVpcPeerings**|GET|查询VpcPeering资源列表|
