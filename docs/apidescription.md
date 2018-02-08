# 易龙平台接口说明

## 简介

### Token获取

```
请求基本地址:http://localhost/token  

参数说明:
{
   client_id:'AA9FE7B3F532084B65816C724D95311A',
   client_secret:'AA9FE7B3F532084B318E0528FD8326E6',
   grant_type:'client_credentials'
}

client_id:我方提供
client_secret:我方提供

请求获取到token后，后续调用接口时需要添加token到请求头的authorization，形式为：  

Authorization:Basic QzFCQzRDQ0VEOEI1NDRG

形式为:Authorization:Basic+空格+token
```

## 模块介绍

### 普通过磅接口说明
```
地址：/api/services/app/table31Order/GetMainObjectForList
```

```
参数：   
{
  "maxResultCount":10,
  "draw":1,
  "sorting":"MyTime",
  "skipCount":0,
  "queryConditionItem":
  [
    {"dataField":"MyTime","op":"GT","dataValue":"0"},
    {"dataField":"OrgId","op":"EQ","dataValue":"48772EA1-1D0D-4388-A6BA-A824010C09C3"}
  ]
    
}
maxResultCount:每页行数
draw:当前页码
skipCount:（当前页码-1）*每页行数
sorting:排序字段(时间戳MyTime)

queryConditionItem:多条件查询
  op:GT为大于EQ为等于
```


```
返回结果：
{
  "data": {
    "success": true,
    "result": {
      "draw": 1,
      "recordsTotal": 1,
      "recordsFiltered": 1,
      "data": [
        {
          "orgId": "48772ea1-1d0d-4388-a6ba-a824010c09c3",
          "orgCode": "",
          "orgName": "",
          "orderDate": "2017-12-08",
          "orderCode": "1500010011712080A00026",
          "orderDataType": 0,
          "orderDataId": "00000000-0000-0000-0000-000000000000",
          "infoNM": "46b7fd8e-f1ab-49a1-ae13-ef88b9a29d98",
          "infoCode": "1104058010015",
          "infoName": "河砂",
          "infoModel": " ",
          "infoUnit": "吨",
          "cId": "0f27e818-417d-473c-864d-cedc77c98147",
          "classNodebh": "001100040058",
          "maker": "测试人员",
          "makerDate": "2017-12-08",
          "orderRemark": "",
          "orderBarCode": "",
          "v_Col11": "京P888888",
          "v_Col12": "重庆铁发北山地产有限公司",
          "v_Col13": "河砂1库",
          "v_Col14": "河砂1库",
          "v_Col15": "",
          "v_Col16": "2017-12-08 15:34:33",
          "v_Col17": "2017-12-08 15:44:37",
          "v_Col18": "2017-12-08 15:44:37",
          "b_Col26": false,
          "b_Col27": true,
          "b_Col28": false,
          "b_Col29": false,
          "b_Col30": true,
          "d_Col36": 0,
          "d_Col37": 0,
          "d_Col38": 0,
          "d_Col39": 0,
          "d_Col40": 0,
          "d_Col41": 0,
          "d_Col42": 0,
          "d_Col43": 0,
          "d_Col44": 0,
          "o_Col36": "555bd69d-0000-0001-8021-04f1c5c405df",
          "o_Col37": "7796a2d1-86e0-49cd-973b-a843009f375e",
          "isAudit": true,
          "auditor": "",
          "auditDate": "",
          "myTime": 20180131152456080,
          "sortCode": 1,
          "id": "0590dbcc-26ef-4a84-b896-a8430100701c",
          "items": [
            {
              "orderId": "0590dbcc-26ef-4a84-b896-a8430100701c",
              "orgId": "48772ea1-1d0d-4388-a6ba-a824010c09c3",
              "itemOrgCode": null,
              "itemDataType": null,
              "itemDataId": "7d37e918-f05c-4665-a660-a8150130ac8e",
              "itemRemark": null,
              "iI_Col1": null,
              "iI_Col2": null,
              "iV_Col3": "车前摄像头",
              "iV_Col4": "入场",
              "iV_Col5": "S1",
              "iV_Col6": "",
              "iO_Col12": "00000000-0000-0000-0000-000000000000",
              "iO_Col13": "00000000-0000-0000-0000-000000000000",
              "sortCode": null,
              "id": "b015c332-5b99-4c9b-a6b7-a8430100701d"
            }
          ]
        }
      ]
    },
    "error": null,
    "unAuthorizedRequest": false
  }
}
```

|字段说明 |类型说明 | 描述  |   
|---------|---------|------ |    
|id     |guid     |主键   |
|orgId     |guid      |组织id   |
|orgName     |string     |组织名称   |
|orderDate     |string     |日期   |
|orderCode     |string     |磅单批次号   |
|orderDataType     |int     |磅单类型 **见表1**   |
|infoNM     |guid     |材料主键   |
|infoCode     |string     |材料编码   |
|infoName     |string     |规格名称   |
|infoModel     |string     |规格型号   |
|infoUnit     |string     |辅单位   |
|cId     |guid     |类别主键   |
|classNodebh     |string     |类别编码   |
|maker     |string     |过磅员   |
|makerDate     |string     |过磅日期   |
|orderRemark     |string     |备注   |
|v_Col11     |string     |车牌号   |
|v_Col12     |string     |供应商名称   |
|v_Col13     |string     |料仓全称   |
|v_Col14     |string     |料仓名称   |
|v_Col15     |string     |主单位   |
|v_Col16      |string     |进场时间   |
|v_Col17      |string     |出场时间   |
|b_Col26     |bool    |是否退料   |
|b_Col27     |bool     |是否出场   |
|b_Col28     |bool     |是否称皮重   |
|b_Col29     |bool     |是否冲红   |
|b_Col30     |bool     |是否上传   |
|b_Col31     |bool     |是否乘法(主辅单位转换运算)   |
|d_Col36     |decimal     |毛重  |
|d_Col37     |decimal     |皮重   |
|d_Col38     |decimal     |转换率   |
|d_Col39     |decimal     |扣率   |
|d_Col40     |decimal     |扣吨   |
|d_Col42     |decimal     |净重(辅单位)   |
|d_Col43     |decimal     |净重(主单位)   |
|o_Col36     |guid     |供应商主键   |
|o_Col37     |guid     |料仓主键   |
|items     |list     |照片信息**见表2**   |

**表1(OrderDataType)**    

|值 |说明 | 描述  |   
|---|-----|------ |  
|0     |普通磅单|   |
|1     |冲红磅单|   |
|2     |补录磅单|   |
|3     |退料磅|   |

**表2照片信息**

|字段说明 |类型说明 | 描述  |   
|---------|---------|------ | 
|itemId     |guid     |照片主键   |
|orderId     |guid     |磅单主键   |
|orgId     |guid     |组织id   |
|iV_Col3     |string     |摄像头位置   |
|iV_Col4     |string     |进场/出场   |
|iV_Col6     |string     |照片信息(base64字符串)   |


照片显示接口和传参方式：

```
地址：api/services/app/Table31Order/ShowImgByItemId?id=C1428120-C913-42D3-91E2-A872012C6184

返回结果：
{
    "data": {
        "success": true, 
        "result": "/9j/4AAQSkZJRgABAQAAAQABAAD/2wDFAAYEBQYFBAYGBQYHBwYIChAKCgkJChQODww", 
        "error": null, 
        "unAuthorizedRequest": false
    }
}
```



### 混凝土出场磅单接口说明

```
地址：/api/services/app/table32Order/GetMainObjectForList
```

```
参数：   
{
  "maxResultCount":10,
  "draw":1,
  "sorting":"MyTime",
  "skipCount":0,
  "queryConditionItem":
  [
    {"dataField":"MyTime","op":"GT","dataValue":"0"},
    {"dataField":"OrgId","op":"EQ","dataValue":"48772EA1-1D0D-4388-A6BA-A824010C09C3"}
  ]
    
}
maxResultCount:每页行数
draw:当前页码
skipCount:（当前页码-1）*每页行数
sorting:排序字段(时间戳MyTime)

queryConditionItem:多条件查询
  op:GT为大于EQ为等于
```

```
返回结果
{
  "data": {
    "success": true,
    "result": {
      "draw": 1,
      "recordsTotal": 1,
      "recordsFiltered": 1,
      "data": [
        {
          "orgId": "ec0d0d88-be0e-4de2-b767-a75b011747d7",
          "orgCode": "",
          "orgName": "",
          "orderDate": "2018-01-29",
          "orderCode": "出补20180100001",
          "orderDataType": 2,
          "orderDataId": "00000000-0000-0000-0000-000000000000",
          "infoNM": "ce0df2ca-0701-477b-9e7a-afa347fe2419",
          "infoCode": "L011055083292",
          "infoName": "自制混凝土",
          "infoModel": "C20",
          "infoUnit": "吨",
          "cId": "00000000-0000-0000-0000-000000000000",
          "classNodebh": "",
          "maker": "超级管理员",
          "makerDate": "2018-01-29",
          "orderRemark": "",
          "orderBarCode": "",
          "v_Col11": "粤A42343",
          "v_Col12": "陕西八建集团公司",
          "v_Col16": "2018-01-29 10:56:36",
          "v_Col17": "2018-01-29 10:56:36",
          "b_Col26": false,
          "b_Col27": false,
          "b_Col28": false,
          "b_Col29": false,
          "b_Col30": false,
          "d_Col36": 333,
          "d_Col37": 44,
          "d_Col38": 0,
          "d_Col39": 1,
          "d_Col40": 0.33,
          "d_Col41": 0,
          "d_Col42": 288.67,
          "d_Col43": 0,
          "o_Col36": "1a4a235f-cb2d-4de6-af8b-a85501230ec7",
          "o_Col37": "00000000-0000-0000-0000-000000000000",
          "o_Col38": "00000000-0000-0000-0000-000000000000",
          "o_Col29": "00000000-0000-0000-0000-000000000000",
          "o_Col30": "00000000-0000-0000-0000-000000000000",
          "isAudit": false,
          "auditor": "",
          "auditDate": null,
          "items":[
                             {
                              "orderId":"0590dbcc-26ef-4a84-b896-a8430100701c",
                              "orgId":"48772ea1-1d0d-4388-a6ba-a824010c09c3",
                              "itemDataId":"7d37e918-f05c-4665-a660-a8150130ac8e",
                              "iV_Col3":"车前摄像头",
                              "iV_Col4":"入场",
                              "iV_Col5":"S1",
                              "iV_Col6":"",
                              "iO_Col12":"00000000-0000-0000-0000-000000000000",
                              "iO_Col13":"00000000-0000-0000-0000-000000000000",
                              "sortCode":null,
                              "id":"b015c332-5b99-4c9b-a6b7-a8430100701d"
                             }
                      }
                     ]
          "myTime": 20180201140321188,
          "sortCode": null,
          "id": "80ac2097-3622-476f-8e90-a87700b4585d"
        }
      ]
    },
    "error": null,
    "unAuthorizedRequest": false
  }
}
```

|字段说明 |类型说明 | 描述  |   
|---------|---------|------ |    
|id     |guid     |主键   |
|orgId     |guid      |组织id   |
|orgName     |string     |组织名称   |
|orderDate     |string     |日期   |
|orderCode     |string     |磅单批次号   |
|orderDataType     |int     |磅单类型 **见表1**   |
|infoNM     |guid     |材料主键   |
|infoCode     |string     |材料编码   |
|infoName     |string     |规格名称   |
|infoModel     |string     |规格型号   |
|infoUnit     |string     |辅单位   |
|cId     |guid     |类别主键   |
|classNodebh     |string     |类别编码   |
|maker     |string     |过磅员   |
|makerDate     |string     |过磅日期   |
|orderRemark     |string     |备注   |
|v_Col11     |string     |车牌号   |
|v_Col12     |string     |用料单位名称   |
|v_Col13     |string     |工号全称   |
|v_Col14     |string     |工号名称   |
|v_Col15     |string     |主单位   |
|v_Col16      |string     |进场时间   |
|v_Col17      |string     |出场时间   |
|v_Col19      |string     |工号编码  |
|b_Col26     |bool    |是否退料   |
|b_Col27     |bool     |是否出场   |
|b_Col28     |bool     |是否称皮重   |
|b_Col29     |bool     |是否冲红   |
|b_Col30     |bool     |是否上传   |
|b_Col31     |bool     |是否乘法(主辅单位转换运算)   |
|d_Col36     |decimal     |毛重  |
|d_Col37     |decimal     |皮重   |
|d_Col38     |decimal     |转换率   |
|d_Col39     |decimal     |扣率   |
|d_Col40     |decimal     |扣吨   |
|d_Col42     |decimal     |净重(辅单位)   |
|d_Col43     |decimal     |净重(主单位)   |
|o_Col36     |guid     |用料单位主键   |
|o_Col37     |guid     |工号主键   |
|items     |list     |照片信息**见表2**   |

**表1(OrderDataType)**    

|值 |说明 | 描述  |   
|---|-----|------ |  
|0     |普通磅单|   |
|1     |冲红磅单|   |
|2     |补录磅单|   |
|3     |退料磅|   |

**表2照片信息**

|字段说明 |类型说明 | 描述  |   
|---------|---------|------ | 
|itemId     |guid     |照片主键   |
|orderId     |guid     |磅单主键   |
|orgId     |guid     |组织id   |
|iV_Col3     |string     |摄像头位置   |
|iV_Col4     |string     |进场/出场   |
|iV_Col6     |string     |照片信息(base64字符串)   |


照片显示接口和传参方式：

```
地址：api/services/app/Table32Order/ShowImgByItemId?id=C1428120-C913-42D3-91E2-A872012C6184

返回结果：
{
    "data": {
        "success": true, 
        "result": "/9j/4AAQSkZJRgABAQAAAQABAAD/2wDFAAYEBQYFBAYGBQYHBwYIChAKCgkJChQODww", 
        "error": null, 
        "unAuthorizedRequest": false
    }
}
```


### 拌合站接口说明

```
地址：/api/services/app/table62Order/GetMainObjectForList
```

```
参数：   
{
  "maxResultCount": 10,
  "draw": 1,
  "sorting": "MyTime",
  "skipCount": 0,
  "queryConditionItem": [
    {
      "dataField": "MyTime",
      "op": "GT",
      "dataValue": "0"
    },
    {
      "dataField": "OrgId",
      "op": "EQ",
      "dataValue": "48772EA1-1D0D-4388-A6BA-A824010C09C3"
    }
  ]
}
maxResultCount:每页行数
draw:当前页码
skipCount:（当前页码-1）*每页行数
sorting:排序字段(时间戳MyTime)

queryConditionItem:多条件查询
  op:GT为大于EQ为等于
```

```
返回结果
{
  "data": {
    "success": true,
    "result": {
      "draw": 1,
      "recordsTotal": 1,
      "recordsFiltered": 1,
      "data": [
        {
          "orgId": "0984e905-50f6-4bfd-9774-a81000be73bb",
          "orgName": "",
          "orderDate": "2018-01-22",
          "orderDataId": "00000000-0000-0000-0000-000000000000",
          "infoNM": "00000000-0000-0000-0000-000000000000",
          "infoName": "c40",
          "cId": "00000000-0000-0000-0000-000000000000",
          "maker": "司帆",
          "makerDate": "2018-01-22",
          "v_Col11": "北岸拌和站",
          "v_Col12": "99356D0C8B294A69B9077446A74C8BA1",
          "v_Col13": "913FCFA643084880B778CA95F599B564",
          "v_Col14": "2018/1/22 21:06:51",
          "v_Col15": "司帆",
          "v_Col16": "临建（生活区门前便道）",
          "d_Col36": 11,
          "d_Col37": 0,
          "d_Col38": 2.75,
          "o_Col36": "00000000-0000-0000-0000-000000000000",
          "o_Col37": "00000000-0000-0000-0000-000000000000",
          "o_Col38": "00000000-0000-0000-0000-000000000000",
          "o_Col29": "00000000-0000-0000-0000-000000000000",
          "o_Col30": "00000000-0000-0000-0000-000000000000",
          "items": [
            {
              "orderId": "80c5826a-3b59-499f-bed4-3f8957bbac60",
              "orgId": "0984e905-50f6-4bfd-9774-a81000be73bb",
              "itemDataId": "00000000-0000-0000-0000-000000000000",
              "iV_Col3": "中砂",
              "iV_Col4": "砂",
              "iD_Col10": 2307,
              "iD_Col11": 2282,
              "iO_Col12": "00000000-0000-0000-0000-000000000000",
              "iO_Col13": "00000000-0000-0000-0000-000000000000",
              "sortCode": null,
              "id": "17158925-f604-4584-b9d9-35f75d8e1437"
            },
            {
              "orderId": "80c5826a-3b59-499f-bed4-3f8957bbac60",
              "orgId": "0984e905-50f6-4bfd-9774-a81000be73bb",
              "itemDataId": "00000000-0000-0000-0000-000000000000",
              "iV_Col3": "大石",
              "iV_Col4": "石子",
              "iD_Col10": 2516,
              "iD_Col11": 2492,
              "iO_Col12": "00000000-0000-0000-0000-000000000000",
              "iO_Col13": "00000000-0000-0000-0000-000000000000",
              "sortCode": null,
              "id": "37db67e3-1a5d-4a22-8268-37848690db88"
            },
            {
              "orderId": "80c5826a-3b59-499f-bed4-3f8957bbac60",
              "orgId": "0984e905-50f6-4bfd-9774-a81000be73bb",
              "itemDataId": "00000000-0000-0000-0000-000000000000",
              "iV_Col3": "小石",
              "iV_Col4": "石子",
              "iD_Col10": 278,
              "iD_Col11": 276,
              "iO_Col12": "00000000-0000-0000-0000-000000000000",
              "iO_Col13": "00000000-0000-0000-0000-000000000000",
              "sortCode": null,
              "id": "b7f62e9f-6612-4a94-85d2-4c0f3952d180"
            },
            {
              "orderId": "80c5826a-3b59-499f-bed4-3f8957bbac60",
              "orgId": "0984e905-50f6-4bfd-9774-a81000be73bb",
              "itemDataId": "00000000-0000-0000-0000-000000000000",
              "iV_Col3": "外加剂2",
              "iV_Col4": "外加剂",
              "iD_Col10": 12.18,
              "iD_Col11": 12.13,
              "iO_Col12": "00000000-0000-0000-0000-000000000000",
              "iO_Col13": "00000000-0000-0000-0000-000000000000",
              "sortCode": null,
              "id": "cd7f2e42-325e-4ba5-b6d2-9208be4a937a"
            },
            {
              "orderId": "80c5826a-3b59-499f-bed4-3f8957bbac60",
              "orgId": "0984e905-50f6-4bfd-9774-a81000be73bb",
              "itemDataId": "00000000-0000-0000-0000-000000000000",
              "iV_Col3": "粉煤灰2",
              "iV_Col4": "粉煤灰",
              "iD_Col10": 365.8,
              "iD_Col11": 363.3,
              "iO_Col12": "00000000-0000-0000-0000-000000000000",
              "iO_Col13": "00000000-0000-0000-0000-000000000000",
              "sortCode": null,
              "id": "eae08143-433c-468a-9800-9db1887d038a"
            },
            {
              "orderId": "80c5826a-3b59-499f-bed4-3f8957bbac60",
              "orgId": "0984e905-50f6-4bfd-9774-a81000be73bb",
              "itemDataId": "00000000-0000-0000-0000-000000000000",
              "iV_Col3": "水",
              "iV_Col4": "水",
              "iD_Col10": 255.8,
              "iD_Col11": 254.2,
              "iO_Col12": "00000000-0000-0000-0000-000000000000",
              "iO_Col13": "00000000-0000-0000-0000-000000000000",
              "sortCode": null,
              "id": "3d58aadf-9fbd-45b5-be33-ce289401b418"
            },
            {
              "orderId": "80c5826a-3b59-499f-bed4-3f8957bbac60",
              "orgId": "0984e905-50f6-4bfd-9774-a81000be73bb",
              "itemDataId": "00000000-0000-0000-0000-000000000000",
              "iV_Col3": "水泥1",
              "iV_Col4": "水泥",
              "iD_Col10": 853,
              "iD_Col11": 848,
              "iO_Col12": "00000000-0000-0000-0000-000000000000",
              "iO_Col13": "00000000-0000-0000-0000-000000000000",
              "sortCode": null,
              "id": "886b08a7-58bc-4faf-a40e-f67d05b9fd97"
            }
          ],
          "myTime": 20180201111139870,
          "sortCode": null,
          "id": "80c5826a-3b59-499f-bed4-3f8957bbac60"
        }
      ]
    },
    "error": null,
    "unAuthorizedRequest": false
  }
}
```

|字段说明 |类型说明 | 描述  |   
|---------|---------|------ |    
|id     |guid     |主键   |
|orgId     |guid      |组织id   |
|orgName     |string     |组织名称   |
|orderDate     |string     |日期   |
|infoName     |string     |混凝土标号   |
|cId     |guid     |类别主键   |
|maker     |string     |值班员   |
|makerDate     |string     |值班日期   |
|v_Col11     |string     |拌合站名称  |
|v_Col12     |string     |调度号   |
|v_Col13     |string     |盘号   |
|v_Col14     |string     |生产时间   |
|v_Col15     |string     |值班员   |
|v_Col16      |string     |浇筑部位   |
|v_Col17      |string     |出场时间   |
|d_Col36     |decimal     |计划生产方量  |
|d_Col37     |decimal     |砂浆方量   |
|d_Col38     |decimal     |盘方量   |
|items     |list     |原材料信息**见表1**   |


**表1原材料信息**

|字段说明 |类型说明 | 描述  |   
|---------|---------|------ | 
|itemId     |guid     |照片主键   |
|orderId     |guid     |磅单主键   |
|orgId     |guid     |组织id   |
|iV_Col3     |string     |材料名称   |
|iV_Col4     |string     |料仓名称   |
|iD_Col10|decimal|施工配比|
|iD_Col10|decimal|实际消耗量|
