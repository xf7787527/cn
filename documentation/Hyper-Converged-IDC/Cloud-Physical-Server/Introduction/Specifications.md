# 产品规格

云物理服务器提供以下实例规格类型：标准计算型、计算效能型Ⅰ、计算效能型Ⅰ(二代)、计算效能型Ⅱ、计算效能型Ⅱ内存型、计算效能型Ⅲ、标准存储型、和标准存储型（二代）、存储效能型Ⅰ。GPU型云物理服务器目前有GPUⅠ、GPUⅡ和GPUⅢ。更多机型即将上线。

<table align="center" >
<table>
    <tr>
        <td align="center"><B>实例规格</B></td> 
        <td align="center"><B>CPU</B></td> 
		    <td align="center"><B>内存</B></td>
		    <td align="center"><B>硬盘</B></td>
		    <td align="center"><B>网卡</B></td>
	    <td align="center"><B>支持RAID模式</B></td>
    </tr>
    <tr>   
        <td align="center"><B>标准计算型<br/>（cps.c.normal）<B></td>
		    <td align="center">Intel E5-2683V4<br/>（2*16物理核 2.1GHz）</td>
		    <td align="center">256G（8*32G）DDR4</td>	
		    <td >2*300GB（SAS）+<br/>2*800GB（SSD）</td>
		    <td align="center">独立管理口1块+<br/>2*10GE网卡</td>
		<td align="center">NO RAID/RAID0/RAID1</td>
    </tr>
    <tr>   
        <td align="center"><B>标准计算型内存型（Ampere）<br/>（cps.c.normal.memory.amp）<B></td>
		    <td align="center">Ampere® Altra® Q80-30 <br/>（2*80物理核 3.0GHz）</td>
		    <td align="center">512GB（8*64G）DDR4</td>
		    <td >1*240GB（SSD）</td>
		    <td align="center">独立管理口1块+<br/>2*25GE网卡</td>
		<td align="center">NO RAID</td>
    </tr>
	  <tr>   
        <td align="center"><B>计算效能型Ⅰ<br/>（cps.c.perf1）<B></td>
		    <td align="center">Intel E5-2683V4<br/>（2*16物理核 2.1GHz）</td>
		    <td align="center">256G（8*32G）DDR4</td>
		    <td >2*300GB（SAS）+<br/>1*4000GB（NVME）</td>
		    <td align="center">独立管理口1块+<br/>2*10GE网卡</td>
		<td align="center">NO RAID</td>
    </tr>
	  <tr>   
        <td align="center"><B>计算效能型Ⅰ超高内存型（Ampere）<br/>（cps.c.perf1.supermemory.amp）<B></td>
		    <td align="center">Ampere® Altra® Q80-30<br/>（2*80物理核 3.0GHz）</td>
		    <td align="center">1024GB（32*32G）DDR4</td>
		    <td >1*3.84TB（NVME）</td>
		    <td align="center">独立管理口1块+<br/>2*25GE网卡</td>
		<td align="center">NO RAID</td>
    </tr>
    <tr>   
        <td align="center"><B>计算效能型Ⅰ(二代)<br/>（cps.c2.perf1）<B></td>
		    <td align="center">Intel Gold-6148<br/>（2*20物理核 2.4GHz）</td>
		    <td align="center">384G（12*32G）DDR4</td>
		    <td >1*240GB（SSD）+<br/>1*2TB（NVME）</td>
		    <td align="center">独立管理口1块+<br/>2*10GE网卡</td>
		<td align="center">NO RAID</td>
    </tr>
    <tr>   
        <td align="center"><B>计算效能型Ⅱ<br/>（cps.c.perf2）<B></td>
		    <td align="center">Intel E5-2683V4<br/>（2*16物理核 2.1GHz）</td>
		    <td align="center">256G（8*32G）DDR4</td>
		    <td >1*240GB（SSD）+<br/>16*960GB（SSD）</td>
		    <td align="center">独立管理口1块+<br/>2*10GE网卡</td>
		<td align="center">NO RAID/RAID0/RAID1/RAID10</td>
    </tr>
    <tr>   
        <td align="center"><B>计算效能型Ⅱ(二代)<br/>（cps.c2.perf2）<B></td>
		    <td align="center">Intel Gold-6267<br/>（2*24物理核 2.6GHz）</td>
		    <td align="center">384G（12*32G）DDR4</td>
		    <td >2*240GB（SSD）+16*960GB（SSD）</td>
		    <td align="center">独立管理口1块+<br/>2*10GE网卡</td>
		<td align="center">NO RAID/RAID0/RAID1/RAID10</td>
    </tr>
    <tr>   
        <td align="center"><B>计算效能型Ⅱ内存型<br/>（cps.c.perf2.memory）<B></td>
		    <td align="center">Intel E5-2683V4<br/>（2*16物理核 2.1GHz）</td>
		    <td align="center">768G（24*32G）DDR4</td>
		    <td >2*960GB（SSD）+<br/>14*960G（SATA）</td>
		    <td align="center">独立管理口1块+<br/>2*10GE网卡</td>
		<td align="center">RAID10</td>
    </tr>
    <tr>   
        <td align="center"><B>计算效能型Ⅲ<br/>（cps.c.perf3）<B></td>
		    <td align="center">Intel E5-2620V4<br/>（2*16物理核 2.1GHz）</td>
		    <td align="center">256G（8*32G）DDR4</td>
		    <td >1*960GB（SSD）+<br/>7*960G（SSD）</td>
		    <td align="center">独立管理口1块+<br/>2*10GE网卡</td>
		<td align="center">RAID5+1hotspare</td>
    </tr>
     <tr>   
        <td align="center"><B>计算超能型Ⅰ（霄龙）<br/>（cps.c2.super1.epyc）<B></td>
		    <td align="center">AMD EPYC-7H12<br/>（2*64物理核 2.6GHz）</td>
		    <td align="center">2048G（32*64G）DDR4</td>
		    <td >1*240GB SSD+<br/>1*3.84T NVMe</td>
		    <td align="center">独立管理口1块+<br/>1*25GE网卡</td>
		<td align="center">NO RAID</td>
    </tr>
    <tr>   
        <td align="center"><B>计算超能型 Ⅱ（霄龙）<br/>（cps.c2.super2.epyc）<B></td>
		    <td align="center">AMD EPYC-7642<br/>（2*48物理核 2.3GHz）</td>
		    <td align="center">384G（12*32G）DDR4</td>
		    <td >2*240GB SSD+<br/>8*1.92T SSD</td>
		    <td align="center">独立管理口1块+<br/>2*25GE网卡</td>
		<td align="center">NO RAID/RAID0/RAID1/RAID10</td>
    </tr>
    <tr>   
        <td align="center"><B>标准存储型<br/>（cps.s.normal）<B></td>
		    <td align="center">Intel E5-2650V4<br/>（2*12物理核 2.2GHz）</td>
		    <td align="center">256G（8*32G）DDR4</td>
		    <td >2*300GB（SAS）+<br/>12*6TB（SATA）</td>
		    <td align="center">独立管理口1块+<br/>2*10GE网卡</td>
		<td align="center">NO RAID</td>
    </tr>
    <tr>   
        <td align="center"><B>标准存储型（二代）<br/>（cps.s2.normal）<B></td>
		    <td align="center">Intel Silver-4116<br/>（2*12物理核 2.1GHz）</td>
		    <td align="center">256G（8*32G）DDR4</td>
		    <td >2*300GB（SAS）+<br/>12*10TB（SATA）</td>
		    <td align="center">独立管理口1块+<br/>2*10GE网卡</td>
		<td align="center">NO RAID/RAID0/RAID1/RAID10</td>
    </tr>
    <tr>   
        <td align="center"><B>存储效能型Ⅰ<br/>（cps.s.perf1）<B></td>
		    <td align="center">Intel E5-2620V4<br/>（2*16物理核 2.1GHz）</td>
		    <td align="center">256G（8*32G）DDR4</td>
		    <td >1*480GB（SSD）+<br/>12*6000G +<br/>1*4TB（NVME）</td>
		    <td align="center">独立管理口1块+<br/>2*10GE网卡</td>
		<td align="center">RAID 5+1hotspare + NO RAID</td>
    </tr>
</table>

GPU型云物理服务器实例规格如下：

<table>
    <tr>
        <td align="center"><B>实例规格</B></td> 
        <td align="center"><B>CPU</B></td> 
		    <td align="center"><B>内存</B></td>
		    <td align="center"><B>硬盘</B></td>
		    <td align="center"><B>网卡</B></td>
	    	<td align="center" ><B>GPU</B></td>
	    <td align="center"><B>支持RAID模式</B></td>
    </tr>
    <tr>   
        <td align="center"><B>GPUⅠ<br/>（cps.gpu.1）<B></td>
		    <td align="center">Intel E5-2683V4<br/>（2*16物理核 2.1GHz）</td>
		    <td align="center">256G（8*32G）DDR4</td>
		    <td >2*300GB（SAS）+<br/>6*960GB（SSD）</td>
		    <td align="center">独立管理口1块+<br/>2*10GE网卡</td>
		<td align="center">NVIDIA P40*4</td>
		<td align="center">NO RAID/RAID0/RAID10</td>
    </tr>
    <tr>   
        <td align="center"><B>GPUⅡ<br/>（cps.gpu.2）<B></td>
		    <td align="center">Intel E5-2650V4<br/>（2*12物理核 2.2GHz）</td>
		    <td align="center">256G（8*32G）DDR4</td>
		    <td >2*300GB（SAS）+<br/>4*4000GB（SATA）</td>
		    <td align="center">独立管理口1块+<br/>2*10GE网卡</td>
		<td align="center">NVIDIA P40*4</td>
		<td align="center">NO RAID/RAID0/RAID10</td>
    </tr>
    <tr>   
        <td align="center"><B>GPUⅢ<br/>（cps.gpu.3）<B></td>
		    <td align="center">Intel E5-2650V4<br/>（2*12物理核 2.2GHz）</td>
		    <td align="center">256G（8*32G）DDR4</td>
		    <td >2*300GB（SAS）+<br/>6*6000GB（SATA）</td>
		    <td align="center">独立管理口1块+<br/>2*10GE网卡</td>
		<td align="center">NVIDIA V100*4</td>
		<td align="center">NO RAID/RAID0/RAID10</td>
    </tr>
</table>
