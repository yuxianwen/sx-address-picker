# sx-address-picker
 [中国省省市区 数据来源](https://github.com/modood/Administrative-divisions-of-China)

 [国家地区来源](https://h5api.m.taobao.com/h5/mtop.cainiao.address.ua.global.area.list/1.0/?jsv=2.5.1&appKey=12574478&t=1712242102859&sign=0a30509ed7f24a5bf58a953d3d908dc2&api=mtop.cainiao.address.ua.global.area.list&v=1.0&dataType=jsonp&type=jsonp&callback=mtopjsonp2&data=%7B%22sn%22%3A%22suibianchuan%22%7D)

# SxAddressPicker 地址选择器
> **组件名：sx-address-picker**

### 介绍

该组件高仿淘宝地址省市区区域的picker交互效果，效果基本一致。



### 安装方式

本组件符合[easycom](https://uniapp.dcloud.io/collocation/pages?id=easycom)规范，`HBuilderX 2.5.5`起，只需将本组件导入项目，在页面`template`中即可直接使用，无需在页面中`import`和注册`components`。

### 基本用法 

更多示例请下载示例安装查看。该组件依赖官方ui组件uni-icons、uni-list、uni-load-more、uni-popup、uni-transition，如果项目本身已导入uni-ui，请忽略。
两个json文件在示例包static文件下，自己引入或自建cdn

```html
<sx-address-picker v-model="addressPopup" @confirm="addressConfirm"/>
```

## API

### Props

| 属性名    | 类型           | 默认值 | 说明                            |
| --------- | -------------- | ------ | ------------------------------- |
| value | Boolean | false | 控制picker是否显示，可使用v-model进行控制。 |
| selected | Array          | []     | 可选，默认回显的选项。 |
| quickCitys | Array | ['上海市', '北京市', '苏州市', '杭州市', '广州市', '深圳市', '南京市', '天津市'] | ✨1.1.0，新增常用城市列表，方便快速选择 |
| quickCountys | Array | ['香港特别行政区', '澳门特别行政区', '台湾', '新加坡', '美国','加拿大'] | ✨1.1.0常用国家/地区列表，方便快速选择 |

### Events

| 事件称名 | 说明                 | 返回参数                                         |
| -------- | -------------------- | ------------------------------------------------ |
| confirm  | 当点击完成选择时发出 | 用户选择完毕/收起菜单，触发confirm事件，event=[] |

### 名人语录

每个人都会有缺陷，就像被上帝咬过的苹果，有的人缺陷比较大，正是因为上帝特别喜欢他的芬芳。——**托尔斯泰（俄国）**
