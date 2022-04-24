### 请求头

请求需要请求头携带ak（公钥）和sign（签名）参数，

| 名称   | 类型     | 描述                             | 是否必填 |
| ---- | ------ | ------------------------------ | ---- |
| ak   | String | 公钥                             | 是    |
| sign | String | 签名，DigestUtils.md5Hex(请求参数+私钥) | 是    |

### 添加设备

##### 请求方式：

POST

##### 请求地址：

http://服务器地址/gateway/mockReceive

##### 请求参数：

| 名称   | 类型     | 描述                            | 是否必填 |
| ---- | ------ | ----------------------------- | ---- |
| type | String | 同步数据的类型：ESTATE_DEVICE_SERVICE | 是    |
| data | List   | 设备数据                          | 是    |

##### 设备数据：

| 名称           | 类型     | 描述                                       | 是否必填 |
| ------------ | ------ | ---------------------------------------- | ---- |
| oid          | String | 设备oid                                    | 是    |
| name         | String | 设备名称                                     | 是    |
| type         | String | 设备类型：CAMERA—摄像头；ACCESS_CONTROL—门禁；ROAD_GATE—道闸 | 是    |
| templateCode | String | 设备二级类型：CAMERA_HAIKANG—海康；CAMERA_DAHUA—大华 | 是    |
| recordStatus | String | 设备在线状态：ONLINE—在线；OFFLINE—离线；UNACTIVATED—未激活 | 是    |
| placeId      | String | 设备区域id                                   | 是    |
| placeName    | String | 设备区域名称                                   | 是    |

##### 请求示例：

```
{
"type":"ESTATE_DEVICE_SERVICE",
"data":[{
            "oid":"88888ffff",
            "name":"测试设备",
            "type":"CAMERA",
            "recordStatus":"OFFLINE",
            "placeId":"1494229770627932161",
            "placeName":"test王",
            "templateCode":"CAMERA_HAIKANG"
        }]
}
```

### 添加车辆入园申请：

##### 请求方式：

POST

##### 请求地址：

http://服务器地址/gateway/mockReceive

##### 请求参数：

| 名称   | 类型     | 描述                               | 是否必填 |
| ---- | ------ | -------------------------------- | ---- |
| type | String | 同步数据的类型：CAR_APPLY_RECORD_SERVICE | 是    |
| data | List   | 车辆入园申请数据                         | 是    |

##### 车辆入园申请数据：

| 名称                 | 类型     | 描述                                       | 是否必填                      |
| ------------------ | ------ | ---------------------------------------- | ------------------------- |
| ownerType          | String | 人员类型：EMPLOYEE—正式员工；SUPPLIER—厂商；OTHER—其他；VISITOR—访客 | 是                         |
| ownerDept          | String | 所属部门                                     | 人员类型OTHER时不填              |
| reportName         | String | 负责人姓名                                    | 人员类型为SUPPLIER,VISITOR时，必填 |
| reportDeptName     | String | 负责人所属部门                                  | 人员类型为SUPPLIER，VISITOR时，必填 |
| ownerName          | String | 车主姓名                                     | 是                         |
| ownerPhone         | String | 车主电话                                     | 是                         |
| type               | String | 车辆类型：EMPLOYEE_CAR—员工车辆；SUPPLIER_CAR—厂商车辆；VISITOR_CAR—访客车辆；COMPANY_CAR—公司车辆；TEMPORARY_CAR—临时车辆 | 是                         |
| licensePlateNumber | String | 车牌号                                      | 是                         |
| applyReason        | String | 申请原因                                     | 是                         |
| startDate          | String | 开始时间                                     | 是                         |
| endDate            | String | 结束时间                                     | 是                         |

##### 请求示例：

```
{
"type":"CAR_APPLY_RECORD_SERVICE",
"data":[{
           "ownerType":"EMPLOYEE",
           "ownerName":"赵六",
           "ownerPhone":"13522753369",
           "type":"EMPLOYEE_CAR",
           "licensePlateNumber":"京Q12345",
           "ownerDept":"IOT",
           "applyReason":"参观",
           "startDate":"2022-02-19 14:48:57",
           "endDate":"2022-03-22 14:48:57" 
        }]
}
```

### 添加通行记录

##### 请求方式：

POST

##### 请求地址：

http://服务器地址/gateway/mockReceive
##### 请求参数：

| 名称   | 类型     | 描述                                       | 是否必填 |
| ---- | ------ | ---------------------------------------- | ---- |
| type | String | 同步数据的类型：ESTATE_ACCESS_CONTROL_PASS_SERVICE | 是    |
| data | List   | 通行记录数据                                   | 是    |

##### 通行记录参数：

| 名称          | 类型     | 描述                                       | 是否必填 |
| :---------- | ------ | ---------------------------------------- | ---- |
| cardId      | String | 人员卡号                                     | 是    |
| oid         | String | 设备oid                                    | 是    |
| deviceType  | String | 设备类型：ACCESS_CONTROL—门禁；ROAD_GATE—道闸；     | 是    |
| passStatus  | String | 通行类型：I—进；O—出                             | 是    |
| passType    | String | 通行类别：FACE—人脸；IC_CARD—IC卡；CR_CODE—二维码     | 是    |
| personId    | String | 人员ID                                     | 是    |
| personName  | String | 人员姓名                                     | 是    |
| personType  | String | 人员类型：EMPLOYEE—员工；SUPPLIER—厂商；BLACKLIST—黑名单；STRANGER—陌生人；VISITOR—访客；OTHER—其他 | 是    |
| warningType | String | 通行状态：SUCCESS—成功；FAIL—失败                  | 是    |
| passTime    | String | 通行时间，格式例如：2022-01-19 12:12:00            | 是    |

##### 请求示例：

	{
	"type":"ESTATE_ACCESS_CONTROL_PASS_SERVICE",
	"data":[{
	      "cardId":"ka0001",
	      "oid":"MJ3293824",
	      "deviceType":"ACCESS_CONTROL",
	      "passStatus":"I",
	      "passType":"CR_CODE",
	      "personId":"1466682829522493442",
	      "personName":"关羽",
	      "personType":"EMPLOYEE",
	      "warningType": "SUCCESS",
	      "passTime": "2022-01-19 12:12:00"
		},{
	      "cardId":"ka0001",
	      "oid":"sd2",
	      "deviceType":"ACCESS_CONTROL",
	      "passStatus":"O",
	      "passType":"CR_CODE",
	      "personId":"1466682829522493442",
	      "personName":"关羽",
	      "personType":"EMPLOYEE",
	      "warningType": "SUCCESS",
	      "passTime": "2022-01-19 15:12:00"
		}]
	}
### 添加通行组

##### 请求方式：

POST

##### 请求地址:

http://服务器地址/gateway/mockReceive
##### 请求参数：

| 名称   | 类型     | 描述                                       | 是否必填 |
| ---- | ------ | ---------------------------------------- | ---- |
| type | String | 同步数据的类型：ESTATE_ACCESS_CONTROL_GROUP_SERVICE | 是    |
| data | List   | 通行组数据                                    | 是    |

##### 通行组参数：

| 名称              | 类型           | 描述    | 是否必填 |
| --------------- | ------------ | ----- | ---- |
| name            | String       | 通行组名称 | 是    |
| periodIdsToBind | List<String> | 通行时间段 | 否    |
| deviceIdsToBind | List<String> | 通行设备  | 否    |

##### 请求示例：

	{
		"type":"ESTATE_ACCESS_CONTROL_GROUP_SERVICE",
		"data":[{
	            "name":"测试通行组",
	            "periodIdsToBind":["1463035984573333506", "1464212760192348162"],
	            "deviceIdsToBind":["1466612192426725377", "1466613236737118209", "1468866757964533761"]
			},{
	          	"name":"测试员工通行组",
	            "periodIdsToBind":["1459080354095353858", "1459075646429515778"],
	            "deviceIdsToBind":["1466612192426725377", "1469234933269217282", "1468866757964533761"]
			}]
	}
### 添加厂商入园申请

##### 请求方式：

POST

##### 请求地址：

http://服务器地址/gateway/mockReceive
##### 请求参数：

| 名称   | 类型     | 描述                                      | 是否必填 |
| ---- | ------ | --------------------------------------- | ---- |
| type | String | 同步数据的类型：ESTATE_ENTRANCE_APPROVE_SERVICE | 是    |
| data | List   | 厂商入园申请数据                                | 是    |

##### 厂商入园申请参数：

| 名称           | 类型     | 描述        | 是否必填 |
| ------------ | ------ | --------- | ---- |
| name         | String | 创建人姓名     | 是    |
| applyId      | String | 申请人（厂商）ID | 是    |
| applyName    | String | 申请人（厂商）姓名 | 是    |
| applyReason  | String | 申请原因      | 是    |
| telephone    | String | 申请人电话     | 是    |
| companyName  | String | 申请人公司名称   | 是    |
| employeeId   | String | 汇报负责人ID   | 是    |
| employeeName | String | 汇报负责人姓名   | 是    |

##### 请求示例：

	{
	  "type": "ESTATE_ENTRANCE_APPROVE_SERVICE",
	  "data": [{
	        "name": "供应商AA",
	        "applyId": "1465869490785501186",
	        "applyName": "供应商AA",
	        "applyReason": "无",
	        "telephone": "15810414584",
	        "companyName": "供应商公司AA",
	        "employeeId": "1466585187819962369",
	        "employeeName": "集团员工"
	 	}]
	}
### 添加黑名单

##### 请求方式：

POST

##### 请求地址：

http://服务器地址/gateway/mockReceive
##### 请求参数：

| 名称   | 类型     | 描述                                       | 是否必填 |
| ---- | ------ | ---------------------------------------- | ---- |
| type | String | 同步数据的类型：ESTATE_SECURITY_BLACKLIST_SERVICE | 是    |
| data | List   | 黑名单数据                                    | 是    |

##### 黑名单参数：

| 名称       | 类型     | 描述                                       | 是否必填                  |
| -------- | ------ | ---------------------------------------- | --------------------- |
| name     | String | 人员姓名                                     | 黑名单类型为STRANGER时，该字段不填 |
| photo    | String | 头像地址                                     | 是                     |
| faceId   | String | 人脸ID                                     | 是                     |
| idNumber | String | 身份证号码                                    | 黑名单类型为STRANGER时，该字段不填 |
| type     | String | 黑名单类型: EMPLOYEE—员工、SUPPLIER—厂商、STRANGER—陌生人、VISITOR—访客 | 是                     |
| extraId  | String | 访客表、员工表 等表主键ID                           | 黑名单类型为STRANGER时，该字段不填 |

##### 请求示例：

	{
	"type": "ESTATE_SECURITY_BLACKLIST_SERVICE",
	"data": [{
		"name": "随行1",
		"photo": "http://xxxx.jpg",
		"faceId": "1466316814753079296",
		"idNumber": "130302199601222222",
		"type": "VISITOR",
		"extraId": "1466317106891616258"
		}]
	}
### 添加人员

##### 请求方式：

POST

##### 请求地址：

http://服务器地址/gateway/mockReceive
##### 请求参数：

| 名称   | 类型     | 描述                              | 是否必填 |
| ---- | ------ | ------------------------------- | ---- |
| type | String | 同步数据的类型：ESTATE_EMPLOYEE_SERVICE | 是    |
| data | List   | 人员数据                            | 是    |

##### 人员参数：

| 名称             | 类型     | 描述                           | 是否必填              |
| -------------- | ------ | ---------------------------- | ----------------- |
| name           | String | 人员姓名                         | 是                 |
| gender         | String | 性别                           | 是                 |
| idNumber       | String | 身份证号                         | 是                 |
| telephone      | String | 电话号码                         | 是                 |
| email          | String | 邮箱号码                         | 是                 |
| deptId         | String | 部门id                         | 是                 |
| deptName       | String | 部门名称                         | 是                 |
| type           | String | 人员类型：EMPLOYEE—员工；SUPPLIER—厂商 | 是                 |
| photo          | String | 照片                           | 是                 |
| cardId         | String | 胸卡卡号                         | 是                 |
| state          | String | 状态，默认EFFECTIVE               | 是                 |
| inDate         | String | 入职时间                         | 是                 |
| outDate        | String | 离职时间                         | 是                 |
| jobNumber      | String | 员工工号                         | 人员类型为EMPLOYEE时，必填 |
| companyName    | String | 公司名称                         | 人员类型为SUPPLIER时，必填 |
| faceId         | String | 人脸id                         | 是                 |
| reportDeptId   | String | 负责人部门id                      | 人员类型为SUPPLIER时，必填 |
| reportDeptName | String | 负责人部门名称                      | 人员类型为SUPPLIER时，必填 |
| reportId       | String | 负责人id                        | 人员类型为SUPPLIER时，必填 |
| reportName     | String | 负责人名称                        | 人员类型为SUPPLIER时，必填 |
##### 请求示例：

	{
	"type":"ESTATE_EMPLOYEE_SERVICE",
	"data":[{
	  	"name": "test王",
	    "gender": "FEMALE",
	    "idNumber": "130633199709340012",
	    "telephone": "13522753369",
	    "email": "001@jd.com",
	    "deptId": "1463400467443441665",
	    "deptName": "IOT",
	    "type": "EMPLOYEE",
	    "photo": "http://xxxx.jpg",
	    "cardId": "card666",
	    "jobNumber":"123321",
	    "state": "EFFECTIVE",
	    "inDate": "2021-01-01 08:00:00",
	    "outDate": "2023-01-01 08:00:00"
	    }]
	}

### 添加空间

##### 请求方式：

POST

##### 请求地址：

http://服务器地址/gateway/mockReceive
##### 请求参数：

| 名称   | 类型     | 描述                           | 是否必填 |
| ---- | ------ | ---------------------------- | ---- |
| type | String | 同步数据的类型：ESTATE_PLACE_SERVICE | 是    |
| data | List   | 空间数据                         | 是    |

##### 空间参数：

| 名称       | 类型     | 描述   | 是否必填 |
| -------- | ------ | ---- | ---- |
| name     | String | 名称   | 是    |
| level    | String | 级别   | 是    |
| parentId | String | 父级id | 是    |

##### 请求示例：

```
{
"type":"ESTATE_PLACE_SERVICE",
"data":[{
  	"name":"16号楼",
  	"level":"2",
  	"parentId":"1494229770627932161"
    }]
}
```

### 添加通行时间段

##### 请求方式：

POST

##### 请求地址：

http://服务器地址/gateway/mockReceive
##### 请求参数：

| 名称   | 类型     | 描述                            | 是否必填 |
| ---- | ------ | ----------------------------- | ---- |
| type | String | 同步数据的类型：ESTATE_PERIOD_SERVICE | 是    |
| data | List   | 通行时间段数据                       | 是    |

##### 通行时间段参数：

| 名称           | 类型     | 描述          | 是否必填 |
| ------------ | ------ | ----------- | ---- |
| name         | String | 名称          | 是    |
| hourFrom     | String | 开始时间点       | 是    |
| hourTo       | String | 结束时间点       | 是    |
| yyyyMMddFrom | String | 开始日期        | 是    |
| yyyyMMddTo   | String | 结束日期        | 是    |
| weeks        | String | 重复日期        | 是    |
| enable       | String | 是否开启，默认true | 是    |

##### 请求示例：

```
{
"type":"ESTATE_PERIOD_SERVICE",
"data":[{
  	"yyyyMMddFrom":"1970-01-01 00:00:00",
  	"yyyyMMddTo":"2100-01-01 00:00:00",
  	"hourFrom":"08:00",
  	"hourTo":"12:00",
  	"weeks":"7,1",
  	"enable":true,
  	"name":"上午通行"
    }]
}
```

### 添加部门

##### 请求方式：

POST

##### 请求地址：

http://服务器地址/gateway/mockReceive
##### 请求参数：

| 名称   | 类型     | 描述                                | 是否必填 |
| ---- | ------ | --------------------------------- | ---- |
| type | String | 同步数据的类型：ESTATE_DEPARTMENT_SERVICE | 是    |
| data | List   | 部门数据                              | 是    |

##### 部门参数：

| 名称         | 类型     | 描述      | 是否必填 |
| ---------- | ------ | ------- | ---- |
| shortName  | String | 部门名称    | 是    |
| sort       | String | 排列序号    | 是    |
| parentName | String | 上级部门名称  | 否    |
| employeeId | String | 部门负责人id | 否    |
| projects   | List   | 关联项目    | 是    |
| parentId   | String | 上级部门id  | 否    |

##### 请求示例：

```
{
"type":"ESTATE_DEPARTMENT_SERVICE",
"data":[{
	"shortName":"商城",
	"sort":"1",
	"parentName":"集团",
	"employeeId":"",
	"projects":[{
		"key":"6218e115ec0e4b60baed90b1702d610c",
		"value":"test王"	
		}],
	"parentId":"0"
    }]
}
```

### 添加车辆通行记录

##### 请求方式：

POST

##### 请求地址：

http://服务器地址/gateway/mockReceive

##### 请求参数：

| 名称   | 类型     | 描述                              | 是否必填 |
| ---- | ------ | ------------------------------- | ---- |
| type | String | 同步数据的类型：ESTATE_CAR_PASS_SERVICE | 是    |
| data | List   | 车辆通行记录数据                        | 是    |

##### 车辆通行记录参数：

| 名称                 | 类型     | 描述   | 是否必填 |
| ------------------ | ------ | ---- | ---- |
| oid                | String | 设备id | 是    |
| licensePlateNumber | String | 车牌号  | 是    |
| inTime             | String | 驶入时间 | 否    |
| outTime            | String | 驶出时间 | 否    |

```
{
  "type":"ESTATE_CAR_PASS_SERVICE",
  "data":[{
    "oid":"MJ3293824",
    "licensePlateNumber": "京A45678", 
    "inTime": "2021-11-24 16:29:19",
    "outTime": "2021-11-26 16:29:19"
  }]
}
```

