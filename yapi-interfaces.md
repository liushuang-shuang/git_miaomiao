# 商品查询系统 YAPI 接口文档

## 1. 商品查询预览卡片接口

### 接口信息
- **接口名称**: 获取商品预览信息
- **接口路径**: `/api/product/preview`
- **请求方式**: GET
- **接口描述**: 获取商品预览卡片信息，包含基本信息和状态

### 请求参数

| 参数名 | 必选 | 类型 | 说明 |
|--------|------|------|------|
| productId | 是 | string | 商品ID |
| storeId | 否 | string | 门店ID |

### 返回示例

```json
{
  "code": 200,
  "message": "success",
  "data": {
    "orderInfo": {
      "status": "不通过",
      "statusType": "reject",
      "store": "Skywalker",
      "storeName": "农家小炒肉",
      "productName": "商品通用门店...等3项",
      "updateTime": "9/Jan/2025 19:20:20"
    },
    "details": {
      "changeType": "变更重要程度",
      "productStatus": "不通过",
      "storeName": "Skywalker", 
      "productName": "农家小炒肉",
      "applyDate": "商品通用门店...等3项",
      "updateDate": "9/Jan/2025 19:20:20"
    }
  }
}
```

### 返回参数说明

| 参数名 | 类型 | 说明 |
|--------|------|------|
| code | int | 状态码 |
| message | string | 返回信息 |
| data | object | 数据对象 |
| data.orderInfo | object | 订单信息 |
| data.orderInfo.status | string | 状态文本 |
| data.orderInfo.statusType | string | 状态类型(reject/pass/pending) |
| data.orderInfo.store | string | 门店名称 |
| data.orderInfo.storeName | string | 商品简称 |
| data.orderInfo.productName | string | 商品名称 |
| data.orderInfo.updateTime | string | 更新时间 |
| data.details | object | 详情信息 |
| data.details.changeType | string | 变更类型 |
| data.details.productStatus | string | 商品状态 |
| data.details.storeName | string | 门店名称 |
| data.details.productName | string | 商品名称 |
| data.details.applyDate | string | 申请内容 |
| data.details.updateDate | string | 更新日期 |

## 2. 商品详情接口

### 接口信息
- **接口名称**: 获取商品详情
- **接口路径**: `/api/product/detail`
- **请求方式**: GET
- **接口描述**: 获取商品完整详情信息

### 请求参数

| 参数名 | 必选 | 类型 | 说明 |
|--------|------|------|------|
| productId | 是 | string | 商品ID |

### 返回示例

```json
{
  "code": 200,
  "message": "success",
  "data": {
    "basicInfo": {
      "salesOrderNo": "892850453985403",
      "salesman": "Miki(V91512973)",
      "applyTime": "2025/Jan/24 12:00:59",
      "changeTime": "2025/Jan/24 12:00:59",
      "businessName": "JAn South Jakarta",
      "businessId": "892850453985403",
      "businessAddress": "South Jakarta",
      "deliveryTime": "9家",
      "isDowngraded": true,
      "downgradeReason": "商品下架(多收有效门店亏失)",
      "updateBefore": "可用门店",
      "discountCategories": [
        {
          "type": "部分门店",
          "count": 20,
          "icon": "info"
        },
        {
          "type": "满少门店",
          "count": 60,
          "icon": "warning"
        },
        {
          "type": "全部门店",
          "count": 100,
          "icon": "success"
        }
      ]
    },
    "storeList": [
      {
        "id": "KFC-前滩店",
        "name": "KFC-前滩店",
        "selected": false
      },
      {
        "id": "KFC-南山店",
        "name": "KFC-南山店",
        "selected": false
      },
      {
        "id": "KFC-前海店",
        "name": "KFC-前海店",
        "selected": false
      },
      {
        "id": "KFC-前湾店",
        "name": "KFC-前湾店",
        "selected": false
      },
      {
        "id": "KFC-前滩店2",
        "name": "KFC-前滩店",
        "selected": false
      },
      {
        "id": "KFC-前滩店3",
        "name": "KFC-前滩店",
        "selected": false
      },
      {
        "id": "KFC-前海店2",
        "name": "KFC-前海店",
        "selected": false
      },
      {
        "id": "KFC-前海店3",
        "name": "KFC-前海店",
        "selected": false
      }
    ]
  }
}
```

### 返回参数说明

| 参数名 | 类型 | 说明 |
|--------|------|------|
| code | int | 状态码 |
| message | string | 返回信息 |
| data | object | 数据对象 |
| data.basicInfo | object | 基本信息 |
| data.basicInfo.salesOrderNo | string | 销售订单号 |
| data.basicInfo.salesman | string | 销售人员 |
| data.basicInfo.applyTime | string | 申请时间 |
| data.basicInfo.changeTime | string | 变更时间 |
| data.basicInfo.businessName | string | 商家名称 |
| data.basicInfo.businessId | string | 商家ID |
| data.basicInfo.businessAddress | string | 商家地址 |
| data.basicInfo.deliveryTime | string | 送达门店数 |
| data.basicInfo.isDowngraded | boolean | 是否降级 |
| data.basicInfo.downgradeReason | string | 降级原因 |
| data.basicInfo.updateBefore | string | 变更前状态 |
| data.basicInfo.discountCategories | array | 折扣分类统计 |
| data.basicInfo.discountCategories[].type | string | 类型名称 |
| data.basicInfo.discountCategories[].count | int | 数量 |
| data.basicInfo.discountCategories[].icon | string | 图标类型 |
| data.storeList | array | 门店列表 |
| data.storeList[].id | string | 门店ID |
| data.storeList[].name | string | 门店名称 |
| data.storeList[].selected | boolean | 是否选中 |

## 3. 商品列表查询接口

### 接口信息
- **接口名称**: 查询商品列表
- **接口路径**: `/api/product/list`
- **请求方式**: POST
- **接口描述**: 根据条件查询商品列表

### 请求参数

| 参数名 | 必选 | 类型 | 说明 |
|--------|------|------|------|
| timeRange | 否 | object | 时间范围 |
| timeRange.startDate | 否 | string | 开始日期 (格式: YYYY-MM-DD) |
| timeRange.endDate | 否 | string | 结束日期 (格式: YYYY-MM-DD) |
| timeRange.lastDays | 否 | int | 最近天数(与日期范围二选一) |
| status | 否 | string | 审核状态(全部/待审核/已通过/已驳回) |
| storeId | 否 | string | 门店ID |
| keyword | 否 | string | 搜索关键词 |
| pageSize | 否 | int | 每页数量，默认20 |
| pageNum | 否 | int | 页码，默认1 |

### 请求示例

```json
{
  "timeRange": {
    "startDate": "2025-01-01",
    "endDate": "2025-01-31"
  },
  "status": "已驳回",
  "storeId": "",
  "keyword": "",
  "pageSize": 20,
  "pageNum": 1
}
```

### 返回示例

```json
{
  "code": 200,
  "message": "success",
  "data": {
    "total": 100,
    "pageSize": 20,
    "pageNum": 1,
    "list": [
      {
        "id": "892850453985403",
        "status": "不通过",
        "statusType": "reject",
        "storeName": "Skywalker",
        "productName": "农家小炒肉",
        "applyContent": "商品通用门店...等3项",
        "updateTime": "9/Jan/2025 19:20:20",
        "changeType": "变更重要程度"
      }
    ]
  }
}
```

### 返回参数说明

| 参数名 | 类型 | 说明 |
|--------|------|------|
| code | int | 状态码 |
| message | string | 返回信息 |
| data | object | 数据对象 |
| data.total | int | 总数量 |
| data.pageSize | int | 每页数量 |
| data.pageNum | int | 当前页码 |
| data.list | array | 数据列表 |
| data.list[].id | string | 商品ID |
| data.list[].status | string | 状态文本 |
| data.list[].statusType | string | 状态类型 |
| data.list[].storeName | string | 门店名称 |
| data.list[].productName | string | 商品名称 |
| data.list[].applyContent | string | 申请内容 |
| data.list[].updateTime | string | 更新时间 |
| data.list[].changeType | string | 变更类型 |

## 4. 门店列表接口

### 接口信息
- **接口名称**: 获取门店列表
- **接口路径**: `/api/store/list`
- **请求方式**: GET
- **接口描述**: 获取所有可用门店列表

### 请求参数

| 参数名 | 必选 | 类型 | 说明 |
|--------|------|------|------|
| keyword | 否 | string | 搜索关键词 |

### 返回示例

```json
{
  "code": 200,
  "message": "success",
  "data": [
    {
      "id": "KFC-前滩店",
      "name": "KFC-前滩店",
      "address": "浦东新区前滩大道",
      "status": "active"
    },
    {
      "id": "KFC-南山店",
      "name": "KFC-南山店",
      "address": "深圳市南山区",
      "status": "active"
    }
  ]
}
```

### 返回参数说明

| 参数名 | 类型 | 说明 |
|--------|------|------|
| code | int | 状态码 |
| message | string | 返回信息 |
| data | array | 门店列表 |
| data[].id | string | 门店ID |
| data[].name | string | 门店名称 |
| data[].address | string | 门店地址 |
| data[].status | string | 门店状态 |

## 状态码说明

| 状态码 | 说明 |
|--------|------|
| 200 | 请求成功 |
| 400 | 请求参数错误 |
| 401 | 未授权 |
| 403 | 禁止访问 |
| 404 | 资源不存在 |
| 500 | 服务器内部错误 |

## 通用错误返回

```json
{
  "code": 400,
  "message": "参数错误：productId不能为空",
  "data": null
}
```