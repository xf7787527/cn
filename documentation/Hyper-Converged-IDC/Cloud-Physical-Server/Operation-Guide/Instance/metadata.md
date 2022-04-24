## 实例元数据

实例元数据是云物理服务器实例的基本信息，包括实例的id、内网IP地址、公网IP地址等，您可以在云物理服务器内通过访问元数据服务来查看该实例的元数据，以便于针对某些元数据进行实例内部的配置或管理。

### 元数据获取方式

1、目前仅私有网络实例支持元数据功能；<br/>
2、从运行实例内部查看所有类别的实例元数据；<br/>
3、支持Windows和linux OS。<br/>

### 查看元数据

1、元数据访问地址：http://169.254.169.254/latest/metadata/[metadata],<br/>
      ①[metadata]替换以下元数据项；<br/>
            例如：curl http://169.254.169.254/latest/metadata/pin <br/>
      ②latest：该参数指访问最新发行版本的metadata。若您不指定发行版本，则默认指向最新发行版本；若京东云云物理服务器产品修改或更新metadata访问路径或返回数据时，您可以指定最早期的发型版本访问metadata；<br/>
      发行版本格式：yyyy-mm-dd，首次发行版本：2021-11-11。若后续元数据项有更新，则新引入发行版本，老的版本依旧保留。<br/>
            例如：curl http://169.254.169.254/2021-11-11/metadata/<br/>

### 元数据信息

- 基本元数据
<table align="center" >
<table>
    <tr>
        <td align="left"><B>元数据</B></td> 
        <td align="left"><B>说明</B></td> 
		    <td align="left"><B>返回示例</B></td>
		    <td align="left"><B>发行版本</B></td>
    </tr>
    <tr>   
		    <td align="left">account-id</td>
		    <td align="left">账户ID</td>
		    <td align="left">"123412341234"</td>
		    <td align="left">2021-11-11</td>
    </tr>
    <tr>   
		    <td align="left">pin</td>
		    <td align="left">客户识别码</td>
		    <td align="leftleft">"jdcloudcustomer"</td>
		    <td align="left">2021-11-11</td>
    </tr>
    <tr>   
		    <td align="left">instance-id</td>
		    <td align="left">实例ID</td>
		    <td align="left">"cps-abcd1234"</td>
		    <td align="left">2021-11-11</td>
    </tr>
    <tr>   
		    <td align="left">instance-type</td>
		    <td align="left">实例规格</td>
		    <td align="left">"cps.c.normal"</td>
		    <td align="left">2021-11-11</td>
    </tr>
    <tr>   
		    <td align="left">instance-name</td>
		    <td align="left">实例名称</td>
		    <td align="left">"jdcloud-cps-instance"</td>
		    <td align="left">2021-11-11</td>
    </tr>
    <tr>   
		    <td align="left">netif-no</td>
		    <td align="left">实例网口数量，单网口显示1，双网口显示2</td>
		    <td align="left">"1|2"</td>
		    <td align="left">2021-11-11</td>
    </tr>
    <tr>   
		    <td align="left">primary-netif-name</td>
		    <td align="left">实例主网口名称，单网口显示bond0，双网口显示eth0</td>
		    <td align="left">"bond0|eth0"</td>
		    <td align="left">2021-11-11</td>
    </tr>
    <tr>   
		    <td align="left">local-ipv4</td>
		    <td align="left">实例内网地址，如果有多个网口，返回主网口的内网IPv4地址；</td>
		    <td align="left">"10.0.x.x"</td>
		    <td align="left">2021-11-11</td>
    </tr>
    <tr>   
		    <td align="left">local-ipv6</td>
		    <td align="left">实例内网地址，如果有多个网口，返回主网口的内网IPv6地址，如果没有设定则显示为“NotAssigned”</td>
		    <td align="left">"CDCD:8475:1111:3900:2020:1111:xxxx:xxxx"</td>
		    <td align="left">2021-11-11</td>
    </tr>
    <tr>   
		    <td align="left">mac</td>
		    <td align="left">实例内网地址，如果有多个网口，返回主网口的内网IPv6地址，如果没有设定则显示为“NotAssigned”</td>
		    <td align="left">"CDCD:8475:1111:3900:2020:1111:xxxx:xxxx"</td>
		    <td align="left">2021-11-11</td>
    </tr>
    <tr>   
		    <td align="left">public-ipv4</td>
		    <td align="left">实例公网IP地址，basic网络显示公网IP地址，vpc网络中如果有多个网口，返回主网口绑定的EIP地址，如果未绑定则显示为“NotBound”</td>
		    <td align="left">"116.x.x.x"</td>
		    <td align="left">2021-11-11</td>
    </tr>
    <tr>   
		    <td align="left">hostname</td>
		    <td align="left">实例主机名，创建时或者最后一次重装后通过控制台设定的值</td>
		    <td align="left">"host-001"</td>
		    <td align="left">2021-11-11</td>
    </tr>
    <tr>   
		    <td align="left">region</td>
		    <td align="left">实例所属地域</td>
		    <td align="left">"cn-north-1"</td>
		    <td align="left">2021-11-11</td>
    </tr>
    <tr>   
		    <td align="left">az</td>
		    <td align="left">实例所属可用区</td>
		    <td align="left">"cn-north-1a"</td>
		    <td align="left">2021-11-11</td>
    </tr>
    <tr>   
		    <td align="left">os-distro</td>
		    <td align="left">实例OS类型</td>
		    <td align="left">"centos|ubuntu|windows"</td>
		    <td align="left">2021-11-11</td>
    </tr>
    <tr>   
		    <td align="left">os-version</td>
		    <td align="left">实例OS版本</td>
		    <td align="left">"CentOS 7.5 64bit"</td>
		    <td align="left">2021-11-11</td>
    </tr>
    <tr>   
		    <td align="left">network-type</td>
		    <td align="left">网络类型</td>
		    <td align="left">"basic|vpc|jdr”</td>
		    <td align="left">2021-11-11</td>
    </tr>
    <tr>   
		    <td align="left">ssh-keye</td>
		    <td align="left">实例创建或者最后一次重装时绑定的密钥公钥指纹，如果没有显示“NotAssigned”</td>
		    <td align="left">"77:0a:65:44:55:25:68:a2:2f:fc:8e:54:53:e1:f5:12"</td>
		    <td align="left">2021-11-11</td>
    </tr>
    <tr>   
		    <td align="left">user-data</td>
		    <td align="left">用户自定义数据，创建时的userdata的base64编码后结果，如果用户没有填入，则显示“NotDefined”</td>
		    <td align="left">"IyEvYmluL2Jhc2gKZWNobyAnaGVsbG8gd29yZCc="</td>
		    <td align="left">2021-11-11</td>
    </tr>  
</table>
  
- 基本元数据<br/>
  说明：network/[primary|secondary] ，指网口信息[主primary/辅secondary]，针对VPC网络有如下这些元数据，统一前缀,单网口时secondary的数据都显示为“NoSecondNetif” 
<table align="center" ><br/>
<table>
    <tr>
        <td align="left"><B>元数据</B></td> 
        <td align="left"><B>说明</B></td> 
		    <td align="left"><B>返回示例</B></td>
		    <td align="left"><B>发行版本</B></td>
    </tr>  
    <tr>   
		    <td align="left">network/[primary|secondary]/local-ipv4</td>
		    <td align="left">实例主/辅网口内网IP地址</td>
		    <td align="left">"172.16.x.x"</td>
		    <td align="left">2021-11-11</td>
    </tr>
    <tr>   
		    <td align="left">network/[primary|secondary]/mac</td>
		    <td align="left">实例主/辅网口mac地址</td>
		    <td align="left">"08:00:20:0A:xx:xx"</td>
		    <td align="left">2021-11-11</td>
    </tr> 
    <tr>   
		    <td align="left">network/[primary|secondary]/public-ipv4</td>
		    <td align="left">实例主/辅网口公网IP地址（网口主IP地址绑定的EIP），如果未绑定则显示为“NotBound”</td>
		    <td align="left">"116.x.x.x"</td>
		    <td align="left">2021-11-11</td>
    </tr>
    <tr>   
		    <td align="left">network/[primary|secondary]/local-ipv6</td>
		    <td align="left">实例主/辅网口内网IPv6地址，如果没有设定则显示为“NotAssigned”</td>
		    <td align="left">"CDCD:8475:1111:3900:2020:1111:xxxx:xxxx"</td>
		    <td align="left">2021-11-11</td>
    </tr>
    <tr>   
		    <td align="left">network/[primary|secondary]/vpc-id</td>
		    <td align="left">实例主/辅网口所属VPC的ID</td>
		    <td align="left">"v91a43d48xxxxxxxx"</td>
		    <td align="left">2021-11-11</td>
    </tr>
    <tr>   
		    <td align="left">network/[primary|secondary]/vpc-cidr-ipv4</td>
		    <td align="left">实例主/辅网口所属VPC的IPv4网段</td>
		    <td align="left">"192.168.x.x/16"</td>
		    <td align="left">2021-11-11</td>
    </tr>
    <tr>   
		    <td align="left">network/[primary|secondary]/vpc-cidr-ipv6</td>
		    <td align="left">实例主/辅网口所属VPC的IPv6网段，如果没有设定则显示为“NotAssigned”</td>
		    <td align="left">"2402:db40:xxxx:xxxx::/60"</td>
		    <td align="left">2021-11-11</td>
    </tr>
    <tr>   
		    <td align="left">network/[primary|secondary]/subnet-id</td>
		    <td align="left">实例主/辅网口所属子网的ID</td>
		    <td align="left">"ndf742cce5axxxxxxxx"</td>
		    <td align="left">2021-11-11</td>
    </tr>
    <tr>   
		    <td align="left">network/[primary|secondary]/subnet-primary-cidr-ipv4</td>
		    <td align="left">实例主/辅网口所属子网的主网段</td>
		    <td align="left">"10.0.0.x/24"</td>
		    <td align="left">2021-11-11</td>
    </tr>
    <tr>   
		    <td align="left">network/[primary|secondary]/subnet-primary-cidr-gateway-ipv4</td>
		    <td align="left">实例主/辅网口所属子网的主网段网关</td>
		    <td align="left">"10.0.0.1"</td>
		    <td align="left">2021-11-11</td>
    </tr>
    <tr>   
		    <td align="left">network/[primary|secondary]/subnet-secondary-cidr-ipv4</td>
		    <td align="left">实例主/辅网口所属子网的辅网段，如果没有设定则显示为“NotAssigned”</td>
		    <td align="left">"10.0.1.x/24"</td>
		    <td align="left">2021-11-11</td>
    </tr>
    <tr>   
		    <td align="left">network/[primary|secondary]/subnet-secondary-cidr-gateway-ipv4</td>
		    <td align="left">实例主/辅网口所属子网的辅网段网关，如果没有设定则显示为“NotAssigned”</td>
		    <td align="left">"10.0.1.1"</td>
		    <td align="left">2021-11-11</td>
    </tr>
    <tr>   
		    <td align="left">network/[primary|secondary]/subnet-primary-cidr-ipv6</td>
		    <td align="left">实例主/辅网口所属子网的主IPv6网段，如果没有显示“NotAssigned”</td>
		    <td align="left">"2402:XXXX:XXXX:c0::/64"</td>
		    <td align="left">2021-11-11</td>
    </tr>
    <tr>   
		    <td align="left">network/[primary|secondary]/subnet-primary-cidr-ipv6-gateway</td>
		    <td align="left">实例主/辅网口所属子网的主IPv6网段网关，如果没有显示“NotAssigned”</td>
		    <td align="left">"2402:XXXX:XXXX:c0::1"</td>
		    <td align="left">2021-11-11</td>
    </tr>
  </table>
