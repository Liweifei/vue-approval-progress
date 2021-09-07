<template>
  <div class="app">
    <vue-approval-progress :data-list="dataList"></vue-approval-progress>
  </div>
</template>

<script>
export default {
  name: "app",
  data() {
    return {
      dataList: [
        {
          title: "sx",
          list: [
            [
              {
                title: "发起人",
                icon: "vapfont vap-top_icon4",
                headportrait: ["https://v3.cn.vuejs.org/logos.png"],
                iconLabel: "发",
                handlerInfo: [
                  {
                    name: "xxx",
                    prefix: "审批人",
                    post: "UI设计师",
                    time: "2021-03-15  20:42:00",
                    approvalType: "",
                  },
                ],
                descPrefixColor:"red",
                descColor:"red",
                descPrefix:"发起说明",
                desc:
                  "转正时间到，申请转正，望领导批准！转正时间到，申请转正，望领导批准！转正时间到，申请转正，望领导批准！",
              },
            ],
          ],
        },
        {
          title: "gf",
          list: [
            [
              {
                title: "",
                headportrait: [
                  "http://wework.qpic.cn/bizmail/yEeLOMJgibZwIUJQXyfdyAaLFIgVjFUzl78HdIJ2eFelFk3hMroghMQ/100",
                  // "http://wework.qpic.cn/bizmail/wM9IumlQibQ6o3epyIZGh3P0VriargcE46pBYL82GqiauxJvF6TbQAgHw/100",
                  // null,
                ],
                handlerInfo: [
                  {
                    name: "xxx",
                    prefix: "审批人",
                    post: "部门主管",
                    time: "2021-03-15  20:42:00",
                    approvalType: "同意",
                  },
                ],
                descPrefix:"审批意见",
                desc:
                  "xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxaaaaaaaaaaaaaaaaaaabbbbbbbbbbbbbbbbbbbbbbbccccccccccccccccccccdddddddddddddddddd",
              },
              {
                title: "",
                headportrait: [
                  "http://wework.qpic.cn/bizmail/yEeLOMJgibZwIUJQXyfdyAaLFIgVjFUzl78HdIJ2eFelFk3hMroghMQ/100",
                ],
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
                descPrefix:"审批意见",
                desc: "该员工任职UI设计师，态度认真，故本人同意转正。",
              },
              {
                title: "",
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
                descPrefix:"审批意见",
                desc: "",
              },
            ],
            [
              {
                title: "会签",
                headportrait: ["https://v3.cn.vuejs.org/logos.png"],
                handlerInfo: [
                  {
                    name: "xxx",
                    prefix: "财务主管",
                    time: "2021-03-15  20:42:00",
                    approvalType: "同意",
                  },
                  {
                    name: "xxx",
                    prefix: "财务主管",
                    time: "2021-03-15  20:42:00",
                    approvalType: "同意",
                  },
                ],
                descPrefix:"审批意见",
                desc: "同意同意",
              },
              {
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
                descPrefix:"审批意见",
                desc: "",
                mark: "第2次审批",
                markColor: "red",
              },
            ],
            [
              {
                title: "抄送人",
                sameLineTime:true,
                disabled:true,
                // icon: "vapfont vap-gou2",
                // headportrait: ["https://v3.cn.vuejs.org/logos.png","https://v3.cn.vuejs.org/logos.png","https://v3.cn.vuejs.org/logos.png"],
                handlerInfo: [
                  {
                    name: "xxx",
                    post: "总裁",
                    // prefix: "总裁",
                    time: "2021-03-15  20:42:00",
                    // approvalType: "",
                    // icon: "vapfont vap-gou2",
                  },
                  {
                    name: "xxx",
                    post: "副总裁",
                    // prefix: "副总裁",
                    time: "2021-03-15  20:42:00",
                    approvalType: "抄送",
                    // icon: "vapfont vap-gou",
                  },
                ],
                descPrefix:"审批意见",
                desc: "",
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
