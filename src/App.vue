<template>
  <div class="app">
    <vue-approval-progress
      :data-list="dataList"
      :over-visible="false"
      :over-disabled="true"
    ></vue-approval-progress>
  </div>
</template>

<script>
export default {
  name: "app",
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
};
</script>

<style lang="scss">
.app {
}
</style>
