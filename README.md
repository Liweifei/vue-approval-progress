## vue-approval-progress(当前版本 V3.0.2)

一款高效、简洁、功能丰富的审批进度流程显示 pc 端插件

## 兼容版本

Vue2.x

## Install

```javascript
	npm i vue-approval-progress -S

	//main.js
	import vap from "vue-approval-progress";
	Vue.use(vap)

	data() {
    return {
      dataList: [
        {
          title: "第二次审批",
          list: [
            [
              {
                // title: "发起人",
                icon: "vapfont vap-top_icon4",
                headportrait: ["https://v3.cn.vuejs.org/logos.png"],
                iconLabel: "发",
                className:"classname",
                handlerInfo: [
                  {
                    name: "xxx",
                    prefix: "审批人",
                    post: "UI设计师",
                    time: "2021-03-15  20:42:00",
                    approvalType: "",
                  },
                ],
                descPrefixColor: "red",
                descColor: "red",
                descPrefix: "发起说明",
                desc:
                  "转正时间到，申请转正，望领导批准！转正时间到，申请转正，望领导批准！转正时间到，申请转正，望领导批准！",
              },
            ],
            [
              {
                title: "会签",
              },
              {
                title: "",
                className:"classname1",
                sameLineTime: true,
                headportrait: [
                  "https://v3.cn.vuejs.org/logos.png",
                  // null,
                ],
                handlerInfo: [
                  {
                    name: "xxx",
                    prefix: "审批人",
                    // post: "部门主管",
                    time: "2021-03-15  20:42:00",
                    approvalType: "同意",
                  },
                ],
                descPrefix: "审批意见",
                desc:
                  "xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxaaaaaaaaaaaaaaaaaaabbbbbbbbbbbbbbbbbbbbbbbccccccccccccccccccccdddddddddddddddddd",
              },
              {
                title: "",
                className:"classname2",
                sameLineTime: true,
                headportrait: ["https://v3.cn.vuejs.org/logos.png"],
                handlerInfo: [
                  {
                    name: "xxx",
                    prefix: "审批人",
                    post: "商务主管",
                    time: "2021-03-15  20:42:00",
                    approvalType: "拒绝",
                    approvalTypeColor: "red",
                    timeColor: "red",
                    stepList: "red",
                  },
                ],
                descPrefix: "审批意见",
                desc: "该员工任职UI设计师，态度认真，故本人同意转正。",
              },
              {
                title: "",
                sameLineTime: true,
                headportrait: ["https://v3.cn.vuejs.org/logos.png"],
                handlerInfo: [
                  {
                    name: "xxx",
                    prefix: "审批人",
                    post: "商务主管",
                    time: "2021-03-15  20:42:00",
                    approvalType: "拒绝",
                    approvalTypeColor: "red",
                    timeColor: "red",
                    stepList: "red",
                  },
                ],
                descPrefix: "审批意见",
                desc:
                  "该员工任职UI设计师，态度认真，故本人同意转正。该员工任职UI设计师，态度认真，故本人同意转正。该员工任职UI设计师，态度认真，故本人同意转正。该员工任职UI设计师，态度认真，故本人同意转正。该员工任职UI设计师，态度认真，故本人同意转正。该员工任职UI设计师，态度认真，故本人同意转正。",
              },
            ],
            [
              { title: "抄送人", sameLineTime: true, disabled: true },
              {
                title: "",
                sameLineTime: true,
                disabled: true,
                headportrait: ["https://v3.cn.vuejs.org/logos.png"],
                handlerInfo: [
                  {
                    name: "xx1",
                    approvalType: "待抄送",
                  },
                ],
              },
              {
                title: "",
                sameLineTime: true,
                disabled: true,
                headportrait: ["https://v3.cn.vuejs.org/logos.png"],
                handlerInfo: [
                  {
                    name: "xx2",
                    approvalType: "待抄送",
                  },
                ],
              },
            ],
            [
              {
                title: "结束",
                last: true,
                disabled: true,
              },
            ],
          ],
        },
        {
          title: "第一次审批",
          list: [
            [
              {
                // title: "发起人",
                sameLineTime: true,
                icon: "vapfont vap-top_icon4",
                headportrait: ["https://v3.cn.vuejs.org/logos.png"],
                iconLabel: "发",
                handlerInfo: [
                  {
                    name: "xxx",
                    prefix: "发起人",
                    post: "UI设计师",
                    time: "2021-03-15  20:42:00",
                    approvalType: "",
                  },
                ],
                descPrefixColor: "red",
                descColor: "red",
                descPrefix: "发起说明",
                desc:
                  "转正时间到，申请转正，望领导批准！转正时间到，申请转正，望领导批准！转正时间到，申请转正，望领导批准！",
              },
            ],
            [
              {
                title: "或签",
              },
              {
                sameLineTime: true,
                headportrait: ["https://v3.cn.vuejs.org/logos.png"],
                handlerInfo: [
                  {
                    name: "xxx",
                    prefix: "财务主管",
                    time: "2021-03-15  20:42:00",
                    approvalType: "同意",
                  },
                ],
                descPrefix: "审批意见",
                desc: "同意同意",
              },
              {
                sameLineTime: true,
                title: "",
                handlerInfo: [
                  {
                    name: "xxx",
                    prefix: "行政主管",
                    time: "2021-03-15  20:42:00",
                    approvalType: "拒绝",
                    approvalTypeColor: "red",
                    timeColor: "red",
                    stepList: "red",
                  },
                ],
                descPrefix: "审批意见",
                desc: "考核不通过",
                descColor: "red",
              },
            ],
            [
              {
                sameLineTime: true,
                title: "",
                handlerInfo: [
                  {
                    name: "发起人撤回",
                    nameColor: "#FF4343",
                    prefix: "",
                    time: "2021-03-15  20:42:00",
                    approvalType: "",
                    approvalTypeColor: "",
                    timeColor: "",
                    stepList: "",
                  },
                ],
                descPrefix: "",
                desc: "",
              },
            ],
            [
              {
                title: "结束",
                last: true,
              },
            ],
          ],
        },
      ],
    };
  },
```

## 示例

```javascript
	<vue-approval-progress :data-list="dataList"></vue-approval-progress>



```

## V3.x 版本 ui 效果图

![效果图](https://raw.githubusercontent.com/Liweifei/vue-approval-progress/master/demo3.jpg)

## V2.x 版本 ui 效果图(请使用 2.0.6)

![效果图](https://raw.githubusercontent.com/Liweifei/vue-approval-progress/master/demo2.jpg)

## V1.x 版本 ui 效果图(请使用 1.1.0)

![效果图](https://raw.githubusercontent.com/Liweifei/vue-approval-progress/master/demo.jpg)

## Attribute

| 属性          | 类型    | 说明                               | 默认(默认值) | 是否必传 |
| ------------- | ------- | ---------------------------------- | ------------ | -------- |
| data-list     | Array   | 流程数据源(下方详细说明)           | true([])     | false    |
| max-row       | Number  | 文字超过多少行显示省略号           | true(5)      | false    |
| over-visible  | Boolean | 数据默认添加结束项                 | true(true)   | false    |
| over-disabled | Boolean | 数据默认添加结束项是否为不可用状态 | true(false)  | false    |
| default-img   | String  | 默认图片                           | true         | false    |

## data-list

| 属性  | 类型               | 说明                               | 是否默认 | 默认值 |
| ----- | ------------------ | ---------------------------------- | -------- | ------ |
| title | String             | 当前流程的 title，如图"第一次审批" |          |        |
| list  | Array （二维数组） | 当前流程数据源(下方详细说明)       |          |

## list

| 属性            | 类型   | 说明                                                                                                         | 是否默认 | 默认值                                             |
| --------------- | ------ | ------------------------------------------------------------------------------------------------------------ | -------- | -------------------------------------------------- |
| title           | String | 当条数据的 title（注意有多个处理人的情况不展示，参考'或签/会签'样式）                                        |          |                                                    |
| className       | String | 当条数据的 class                                                                                             |          |                                                    |
| sameLineTime    | String | 当条数据的时间是否和用户信息展示在同一行                                                                     |          |                                                    |
| disabled        | String | 当前数据字体等置灰                                                                                           |          |                                                    |
| descPrefix      | String | 当条数据的文字说明前缀                                                                                       | true     | 备注说明                                           |
| descPrefixColor | String | 当条数据的文字说明前缀字体颜色                                                                               | true     | #424675                                            |
| desc            | String | 当条数据的文字说明展示                                                                                       |          |
| descColor       | String | 当条数据的文字说明字体颜色                                                                                   | true     | #424675                                            |
| headportrait    | Array  | 头像显示，当存在 headportrait 值时，会优先于 label 和 icon 的显示                                            |          |                                                    |
| icon            | String | 当条数据的图标展示（注意有多个处理人的情况不展示，参考'或签/会签'样式），若存在 iconLabel 则不展示 icon 图标 | true     | 第一条数据默认人头，结尾数据默认打勾，其它默认印章 |
| iconLabel       | String | 当条数据的图标替换成文字（注意有多个处理人的情况不展示，参考'或签/会签'样式；注意传此则不展示 icon）         |          |
| handlerInfo     | Array  | 当条数据的处理人信息，可传多条(下方详细说明)                                                                 |          |                                                    |

## handlerInfo

| 属性              | 类型   | 说明                     | 是否默认 | 默认值  |
| ----------------- | ------ | ------------------------ | -------- | ------- |
| prefix            | String | 处理人文字前缀           |          |         |
| name              | String | 处理人文字说明           |          |         |
| nameColor         | String | 处理人文字颜色           |          |         |
| post              | String | 处理人职务               |          |         |
| time              | String | 处理时间                 |          |         |
| timeColor         | String | 处理时间文字颜色         | true     | #999999 |
| approvalType      | String | 处理状态文字说明         |          |
| approvalTypeColor | String | 处理状态文字颜色         | true     | #07c264 |
| icon              | String | 处理人后面跟的 icon 图标 |          |         |

## API

| 函数名 | 说明     | 参数格式 | 调用示例               |
| ------ | -------- | -------- | ---------------------- |
| init   | 手动更新 |          | this.$refs.vap.init(); |

## Other

1、后继会继续更新 vue3 版本

2、如果有其他问题邮件沟通1195669615@qq.com或者加 qq1195669615。若插件能够帮助到您，期待您的 star 哦！

3、欢迎加入 qq 交流群（目前正在起步中）

![qq交流群](./qshare.jpg)
