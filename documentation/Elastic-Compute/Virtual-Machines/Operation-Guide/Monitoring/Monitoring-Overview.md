# 监控与报警概述
实例监控与报警为您提供实时实例监控管理服务，支持不同监控维度，在实例成功创建后即开始采集数据，以图表方式直观展现，方便您掌握实例资源使用情况、运行状态等信息，同时您可设置不同的报警规则，当触发该类条件后则触发报警通知，使您轻松定位故障。

## 监控指标
京东云为您提供云主机实例的CPU、内存、磁盘、网络等类型的监控指标，其中云主机监控指标分为基础指标和扩展指标：
* **基础指标**具有较高的通用性，能满足您平时对监控数据的需求，上报的指标种类不支持调整，可在云主机详情页或 云监控-资源监控-云主机 下查看监控数据；
* **扩展指标**是对基础指标的细节补充，可以满足某些特殊场景的监控需求，您需要按需自行配置上报的指标种类，此类指标会上报至 [云监控-自定义监控](https://docs.jdcloud.com/monitoring/custom-monitoring-overview) 服务中，您可以参照下方 [扩展指标配置说明](monitoring-overview#user-content-1) 进行配置，监控数据查看方式请参见 [获取实例监控数据](https://docs.jdcloud.com/virtual-machines/get-monitor-data)。

### 基础指标 
<table>
	<thead>
    <tr>
	    <th>指标类型</th>
	    <th>指标英文名</th>
        <th>指标中文名</th>
      	<th>单位</th>
      	<th>说明</th>
        <th>上报维度</th>
    </tr>
	</thead>
	<tbody>
        <tr>
            <td rowspan="4">CPU</td>
            <td>vm.cpu.util</td>
            <td>CPU使用率</td>
            <td> % </td>
            <td> 非空闲vCPU所占的百分比</td>
            <td> 实例 </td>   
        </tr>
        <tr>
            <td>vm.avg.load1</td>
            <td> CPU平均负载（1min）</td>
            <td> 无 </td>    
            <td> 1分钟内的系统平均负载<br>仅Linux系统有此指标</td>
            <td> 实例</td>
        </tr>
        <tr>
            <td>vm.avg.load5</td>
            <td> CPU平均负载（5min）</td>
            <td> 无 </td>     
            <td> 5分钟内的系统平均负载<br>仅Linux系统有此指标</td>
            <td> 实例 </td>
        </tr>
        <tr>
            <td>vm.avg.load15</td>
            <td> CPU平均负载（15min）</td>
            <td> 无 </td>
            <td> 15分钟内的系统平均负载<br>仅Linux系统有此指标 </td>    
            <td> 实例</td>
        </tr>
        <tr>
            <td rowspan="2">内存</td>
            <td>vm.memory.usage</td>
            <td>内存使用率</td>
            <td> % </td>
            <td> 已用内存量占总内存总量百分比</td>
            <td> 实例 </td>   
        </tr>
        <tr>
            <td>vm.memory.used.bytes</td>
            <td>内存使用量</td>
            <td> Bytes </td>
            <td> 系统已用内存容量</td>
            <td> 实例 </td>   
        </tr>
        <tr>
            <td rowspan="9">磁盘</td>
            <td>vm.disk.bytes.read</td>
            <td>磁盘读吞吐量（Host）<sup>*</sup></td>
            <td> Bps </td>
            <td> 全部磁盘每秒读取的字节数</td>
            <td> 实例 </td>   
        </tr>
        <tr>
            <td>vm.disk.bytes.write</td>
            <td>磁盘写吞吐量（Host）<sup>*</sup></td>
            <td> Bps </td>
            <td> 全部磁盘每秒写入的字节数</td>
            <td> 实例 </td>   
        </tr>
        <tr>
            <td>vm.disk.dev.bytes.read</td>
            <td> 磁盘读吞吐量</td>
            <td> Bps </td>
            <td> 磁盘每秒读取的字节数</td>
            <td rowspan="4"> 设备文件名：devName <br><li type='disc'>Linux：'devName'='/vda','/vdb1', ...</li> <li type='disc'>Windows：‘devName’='C','D', ...</li><br> Linux系统如磁盘有分区，则按分区统计上报，若无分区则按磁盘统计上报；Windows系统均按盘符统计上报。</td>
        </tr>
        <tr>
            <td>vm.disk.dev.bytes.write</td>
        <td>磁盘写吞吐量</td>
        <td> Bps </td>
            <td> 磁盘每秒写入的字节数</td>
        </tr>	
        <tr>
            <td> vm.disk.dev.io.read</td>
            <td> 磁盘读IOPS </td>
            <td> Count/s</td> 
            <td> 磁盘每秒读请求数量</td>
        </tr> 
        <tr>
            <td> vm.disk.dev.io.write</td>
            <td> 磁盘写IOPS </td>
            <td>Count/s</td> 
            <td>磁盘每秒写请求数量</td>
        </tr>
        <tr>
            <td>vm.disk.dev.used</td>
            <td> 磁盘使用率 </td>
            <td>%</td>
            <td>磁盘已使用空间容量</td> 
            <td rowspan="3"> 挂载点：mountPoint <br><li type='disc'>Linux:'mountPoint'='/','/mnt', ...</li> <li type='disc'>Windows:‘mountPoint’='C','D', ...</li><br> Linux系统按挂载点统计上报；Windows系统按盘符统计上报
    仅Linux系统提供'磁盘inode使用率'指标</td>
        </tr>
        <tr>
            <td> vm.disk.dev.used.bytes</td>
            <td>磁盘使用量 </td>
            <td>Bytes </td> 
            <td>磁盘已使用空间容量</td>
        </tr>
        <tr>
            <td> vm.disk.dev.inode.used</td>
            <td>磁盘inode使用率</td>
            <td>%</td> 
            <td>磁盘文件系统inode使用百分比<br>仅Linux系统有此指标</td>
        </tr>
        <tr>
            <td rowspan="7">网络</td>
            <td>vm.network.bytes.incoming </td>
            <td>网络入带宽（Host）<sup>*</sup></td>
            <td>bps</td> 
            <td>全部网卡每秒接收的比特数</td>
            <td>实例</td>
        </tr>
        <tr>
            <td>vm.network.bytes.outgoing</td>
            <td> 网络出带宽（Host）<sup>*</sup></td>
            <td>bps</td> 
            <td>全部网卡每秒接收的比特数</td>
            <td>实例</td>
        </tr>
        <tr>
            <td> vm.network.dev.bytes.in </td>
            <td>网络入带宽</td>
            <td>bps</td> 
            <td>网卡每秒接收的比特数</td>
            <td rowspan="4">网卡：devName <br><li type='disc'>Linux/Windows：'devName'='eth0','eth1', ...</li> </td>
        </tr>
        <tr>
            <td> vm.network.dev.bytes.out </td>
            <td>网络出带宽</td>
            <td>bps</td> 
            <td> 网卡每秒发送的比特数</td>
        </tr>
        <tr>
            <td>vm.network.dev.packets.in </td>
            <td> 网络入包量</td>
            <td>pps</td> 
            <td> 网卡每秒入包量</td>
        </tr>
        <tr>
            <td>vm.network.dev.packets.out </td>
            <td> 网络出包量 </td>
            <td>pps</td> 
            <td>网卡每秒出包量</td>
        </tr>
        <tr>
            <td>vm.netstat.tcp.established </td>
            <td> TCP连接数  </td>
            <td>Count</td> 
            <td>处于 ESTABLISHED 状态的 TCP 连接数量</td>
            <td>实例</td>
        </tr>
        <tr>
            <td rowspan="7">GPU</td>
            <td>vm.gpu.power </td>
            <td> GPU功耗   </td>
            <td>Wt</td> 
            <td>GPU功耗 </td>
            <td rowspan="7">GPU卡：gpu_index <br><li type='disc'>Linux/Windows:'gpu_index'='0','1', ...</li></td>
        </tr>
        <tr>
            <td>vm.gpu.temperature</td>
            <td> GPU温度   </td>
            <td>℃</td> 
            <td>GPU温度 </td>
        </tr>
        <tr>
            <td>vm.gpu.util.gpu</td>
            <td> GPU核心使用率   </td>
            <td>%</td> 
            <td>GPU核心使用率 </td>
        </tr>
        <tr>
            <td>vm.gpu.util.encoder</td>
            <td> GPU编码器使用率   </td>
            <td>%</td> 
            <td>GPU编码器使用率 </td>
        </tr>
        <tr>
            <td>vm.gpu.util.decoder</td>
            <td> GPU解码器使用率   </td>
            <td>%</td> 
            <td>GPU解码器使用率 </td>
        </tr>	
        <tr>
            <td>vm.gpu.util.mem</td>
            <td> GPU内存使用率   </td>
            <td>%</td> 
            <td>GPU内存使用率 </td>
        </tr>	
        <tr>
            <td>vm.gpu.used.mem.bytes</td>
            <td> GPU内存使用量   </td>
            <td>Bytes</td> 
            <td>GPU内存使用量 </td>
        </tr>	
	</tbody>
</table> 

### 扩展指标 
<table>
	<thead>
        <tr>
            <th>指标类型</th>
            <th>指标英文名</th>
            <th>指标中文名</th>
            <th>单位</th>
            <th>说明</th>
            <th>上报维度</th>
        </tr>
	</thead>
	<tbody>
        <tr>
            <td rowspan="2">CPU</td>
            <td>vm.cpu.cores.user</td>
            <td> CPU使用率（user） </td>
            <td> % </td>
            <td> CPU在用户态进程和低优先级进程的时间百分比<br>仅Linux系统有此指标</td>    
            <td> 实例 </td>
        </tr>
        <tr>
            <td>vm.cpu.cores.iowait</td>
            <td> CPU使用率（iowait）</td>
            <td> % </td>
            <td> CPU由于系统IO而处于等待状态的时间百分比<br>仅Linux系统有此指标</td>    
            <td>实例</td>
        </tr>	  	  
        <tr>
            <td rowspan="2">磁盘</td>
            <td> vm.disk.dev.io.util</td>
            <td>磁盘IO繁忙百分比</td>
            <td>%</td> 
            <td>磁盘IO繁忙百分比</td>
            <td rowspan="2">设备名：devName <br><li type='disc'>Linux:'devName'='/vda','/vdb1', ...</li> <li type='disc'>Windows:‘devName’='C','D', ...</li><br> Linux系统如磁盘有分区，则按分区统计上报，若无分区则按磁盘统计上报；Windows系统均按盘符统计上报。</td>
        </tr>
        <tr>
            <td> vm.disk.dev.io.await </td>
            <td>磁盘IO等待百分比</td>
            <td>%</td> 
            <td>磁盘IO等待百分比</td>
        </tr>
    <tr>
            <td rowspan="6">TCP连接数</td>
            <td>vm.netstat.tcp.last_ack </td>
            <td> last_ack </td>
            <td>Count</td> 
            <td>处于last_ack状态下的TCP连接数量</td>
            <td>实例</td>
        </tr>	
        <tr>
            <td>vm.netstat.tcp.syn_recv </td>
            <td>  syn_recv </td>
            <td>Count</td> 
            <td>处于syn_recv状态下的TCP连接数</td>
            <td>实例</td>
        </tr>
        <tr>
            <td>vm.netstat.tcp.fin_wait1 </td>
            <td> fin_wait1 </td>
            <td>Count</td> 
            <td>处于fin_wait1状态下的TCP连接数量</td>
            <td>实例</td>
        </tr>
        <tr>
            <td>vm.netstat.tcp.fin_wait2 </td>
            <td> fin_wait2 </td>
            <td>Count</td> 
            <td>处于fin_wait2状态下的TCP连接数量</td>
            <td>实例</td>
        </tr>
        <tr>
            <td>vm.netstat.tcp.closing </td>
            <td> closing </td>
            <td>Count</td> 
            <td>处于closing状态下的TCP连接数量</td>
            <td>实例</td>
        </tr>
        <tr>
            <td>vm.netstat.tcp.time_wait </td>
            <td> time_wait</td>
            <td>Count</td> 
            <td>处于time_wait状态下的TCP连接数量</td>
            <td>实例</td>
        </tr>
	</body>
</table>

## 扩展指标配置说明

您可以按照下方步骤进行扩展指标的采集配置：

  * 确认JCS-Agent组件版本不低于'3.0.1086'，如低于此版本请参考下方【监控插件安装说明】部分安装或更新插件。
```Shell
    ps -ef|grep MonitorPlugin
```
  * 登录云主机，进入监控插件目录
```Shell
    cd /usr/local/share/jcloud/agent/plugins/MonitorPlugin-[version]
```
  * 创建名称为“Extended.cfg”的配置文件，然后参考下方配置示例，根据需求自定义上报的监控指标，其中：
    * "namespace"：为上报至云监控自定义监控的命名空间，可自定义。
    > namespace长度不可超过255字节，只允许英文、数字、下划线_、点., [0-9][a-z] [A-Z] [. _ ]）。
    * "metrics"：为上报至云监控的扩展指标，目前支持的扩展指标类别包扩："cpu", "disk-io", "netstat" 。
```JSON
{
	"agent": {
		"namespace": "vm_extend_metric"
	},
	"metrics": {
		"disk-io": {
			"measurement-white-list": [
				"vm.disk.dev.io.util",
				"vm.disk.dev.io.await"
			]
		},
		"netstat": {
			"measurement-white-list": [
				"vm.netstat.tcp.last_ack",
				"vm.netstat.tcp.syn_recv",
				"vm.netstat.tcp.fin_wait1",
				"vm.netstat.tcp.fin_wait2",
				"vm.netstat.tcp.closing",
				"vm.netstat.tcp.time_wait",
				"vm.netstat.tcp.retrans_segs"
			]
		},
		"cpu": {
			"measurement-white-list": [
				"vm.cpu.cores.user",
				"vm.cpu.cores.iowait"
			]
		}
	}
}
```
  * 重启监控插件（查找进程id，kill后插件将在5分钟内自动拉起），随后即以上述配置开始采集和上报扩展指标（插件升级期间基础指标可能存在短暂缺失）。
```Shell
      ps -ef | grep -i MonitorPlugin  //查看监控进程id
      kill [pid]  //指定进程id kill   
```
 ## 监控插件安装说明

云主机监控数据的采集和上报依赖于官方镜像系统组件'JCS-Agent'中的'MonitorPlugin'插件，当前官方镜像均默认安装'ifrit'工具，实现对JCS-Agent的自动升级。
如您基础指标或扩展指标监控数据缺失，可能是由于JCS-Agent/ifrit状态异常或版本过低，请确认JCS-Agent/ifrit状态及版本。

> 注意：<br>
> 'MonitorPlugin'插件版本需不低于“3.0.1086”才支持扩展指标的上报

* 关于安装JCS-Agent及Ifrit，您可以参考：[官方镜像系统组件-'JCS-Agent'](https://docs.jdcloud.com/cn/virtual-machines/default-agent-in-public-image#user-content-1)
* JCS-Agent版本查看方式：
  * Linux：` ps -ef|grep MonitorPlugin`
  * Windows：`wmic process where caption="MonitorPlugin.exe" get caption,commandline /value`
  
 
 ## 监控数据说明
* 名称中有“（Host）”字样的指标为云主机所在宿主机采集并上报，其余指标均为系统组件采集上报；
* 所有网络监控指标均不区分内外网，即为内网+外网的整体数据；
* 监控数据采集周期为10s，最小展示间隔为1min；
* 不同指标的默认聚合方式不同，可在监控图中查看各指标的聚合方式；
* 统计周期默认支持1小时、6小时、12小时、1天、3天、7天及14天，此外还支持您设置统计周期，最短为1分钟，最长为一个月。不同统计周期监控值会做对应聚合，例如6小时统计周期情况下，监控图上间隔5分钟显示一个监控值，该监控值为对应统计周期内采集值的聚合，当前仅支持以默认聚合方式查询；
* 监控数据最长保存30天，用户在控制台可以查看30天的监控数据。

## 监控指标单位
单位是监控指标的基本度量，下方为云监控所支持的指标单位：
<table>
	<thead>
    <tr>
	<th>单位</th>
	<th>说明</th>
    </tr>
	</thead>
	<body>
    <tr>
	<td>%</td>
	<td>百分比</td>
    </tr>
    <tr>
	<td>Bytes</td>
	<td>字节数，用于表示数据的大小。1Byte = 8bit</td>
    </tr>
    <tr>
	<td>Bps</td>
	<td>每秒字节数（bytes per second）</td>
    </tr>
    <tr>
	<td>bps</td>
	<td>每秒比特数（bits per second）</td>
    </tr>
    <tr>
	<td>pps</td>
	<td>每秒包数（packets per second）</td>
    </tr>
    <tr>
	<td>Count</td>
	<td>次数</td>
    </tr>
    <tr>
	<td>Count/s</td>
	<td>每秒操作的次数（counts per second）</td>
    </tr>
    <tr>
	<td>Wt</td>
	<td>电功率，每秒消耗的电能</td>
    </tr>
    <tr>
	<td>℃</td>
	<td>摄氏度</td>
    </tr>
	</body>
</table>

## 相关参考
[官方镜像系统组件](https://docs.jdcloud.com/cn/virtual-machines/default-agent-in-public-image)

[获取实例监控数据](https://docs.jdcloud.com/cn/virtual-machines/get-monitor-data)

[云监控-自定义监控](https://docs.jdcloud.com/cn/monitoring/custom-monitoring-overview)

 
   
