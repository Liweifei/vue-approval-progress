<template>
  <div class="vue-approval-progress">
    <div class="stepList" v-for="(stepList, sIndex) in stepList" :key="'s' + sIndex">
      <div class="markInfo" v-if="stepList.title">
        <span class="msg">{{ stepList.title }}</span>
      </div>
      <div
        class="stepItem"
        :class="{ mulStep: list.length > 1 }"
        v-for="(list, lIndex) in stepList.list"
        :key="'k' + sIndex + lIndex"
      >
        <div
          class="itemBox"
          :class="[
            !item.last && !item.desc ? 'noMsg' : null,
            item.disabled ? 'disabled' : null,
            item.className
          ]"
          v-for="(item, index) in list"
          :key="index"
        >
          <div
            class="iconBox"
            :class="{
              isImg: Array.isArray(item.headportrait) && item.headportrait.length > 0,
            }"
          >
            <template
              v-if="Array.isArray(item.headportrait) && item.headportrait.length > 0"
            >
              <div
                class="imgBox"
                v-for="(imgItem, imgIndex) in item.headportrait"
                :key="imgIndex"
              >
                <img
                  :src="imgItem ? imgItem : imgOnError(item, imgIndex)"
                  @error="imgOnError(item, imgIndex)"
                />
              </div>
            </template>
            <span
              class="iconLabel"
              :title="item.iconLabel"
              v-else-if="item.iconLabel"
              v-text="item.iconLabel"
            ></span>
            <i
              v-else
              :class="[
                item.icon
                  ? item.icon
                  : lIndex === 0
                  ? 'vapfont vap-top_icon4'
                  : item.last
                  ? 'vapfont vap-gou'
                  : 'vapfont vap-top_icon4',
              ]"
            ></i>
          </div>
          <div class="r" :class="item.headportraitLh ? `r${item.headportraitLh}` : null">
            <h2 :class="{ isFinished: item.last }" v-if="item.title">{{ item.title }}</h2>
            <div
              class="userInfoBox"
              :class="{ sameLineTime: item.sameLineTime }"
              v-for="(infoItem, iIndex) in item.handlerInfo"
              :key="iIndex"
            >
              <div class="nameBox">
                <span class="prefix" v-show="infoItem.prefix">{{ infoItem.prefix }}</span>
                <span
                  class="name"
                  :style="{
                    color: infoItem.nameColor,
                  }"
                  v-show="infoItem.name"
                  >{{ infoItem.name }}</span
                >
                <span class="post" v-show="infoItem.post" :title="infoItem.post">{{ infoItem.post }}</span>
                <i :class="infoItem.icon" v-if="infoItem.icon"></i>
                <span
                  class="state"
                  :style="{
                    color: infoItem.approvalTypeColor,
                  }"
                  >{{ infoItem.approvalType }}</span
                >
              </div>
              <span
                class="time"
                v-show="infoItem.time"
                :style="{
                  color: infoItem.timeColor,
                }"
                >{{ infoItem.time }}</span
              >
            </div>
            <div
              class="content"
              :class="{ contentVisible: item.show && item.haveBtn }"
              v-if="!item.last && item.desc"
            >
              <p
                class="prefix"
                :style="{
                  color: item.descPrefixColor,
                }"
              >
                {{ item.descPrefix ? item.descPrefix : "备注说明" }}：
              </p>
              <p
                class="main"
                :keyindex="sIndex + '-' + lIndex + '-' + index"
                ref="fillText"
                :style="{
                  color: item.descColor,
                }"
              >
                {{ item.desc }}
              </p>
              <span class="showBtn" v-if="item.haveBtn" @click="showContent(item)">
                {{ item.show ? "收起" : "展开" }}
              </span>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import ImgBase64 from "../src/assets/imgError";
export default {
  name: "vue-approval-progress",
  data() {
    return {
      stepList: [],
    };
  },
  props: {
    dataList: {
      type: Array,
      default: () => {
        return [];
      },
    },
    maxRow: {
      type: Number,
      default: 5,
    },
    overVisible: {
      type: Boolean,
      default: true,
    },
    overDisabled: {
      type: Boolean,
      default: false,
    },
    defaultImg: {
      type: String,
      default: "",
    },
  },
  watch: {
    dataList: {
      handler() {
        this.init();
      },
      immediate: true,
    },
    maxRow: {
      handler() {
        this.init();
      },
    },
    overVisible: {
      handler() {
        this.init();
      },
    },
    overDisabled: {
      handler() {
        this.init();
      },
    },
  },
  methods: {
    init() {
      this.stepList = JSON.parse(JSON.stringify(this.dataList));
      this.formatData();
    },
    formatDom() {
      const fliterTextDom = this.$refs.fillText;
      if (!fliterTextDom) return;
      const compareH = this.maxRow * 20;
      fliterTextDom.forEach((item) => {
        const key = item.getAttribute("keyindex").split("-");
        const io = item.scrollHeight > compareH;
        let stepList = this.stepList[key[0]].list[key[1]][key[2]];
        const headportrait = stepList.headportrait;
        if (headportrait && !Array.isArray(headportrait)) {
          throw "headportrait muse be of Array type";
        }
        Object.assign(stepList, {
          backup: stepList.desc,
          lh: stepList.desc.length,
          haveBtn: io,
          show: io ? false : true,
          ellipsisLh: 6,
        });
        if (io) {
          this.initRowText(item, key);
        }
      });
    },
    initRowText(dom, key) {
      let current = this.stepList[key[0]].list[key[1]][key[2]];
      const compareH = this.maxRow * 20;
      const desc = current.desc;
      if (dom.scrollHeight > compareH) {
        current.lh--;
        current.desc = desc.substring(0, current.lh);
        this.$nextTick(() => {
          this.initRowText(dom, key);
        });
      } else {
        this.addEllipsis(current);
      }
    },
    addEllipsis(current) {
      const { ellipsisLh, desc } = current;
      if (ellipsisLh <= 0) {
        //截取的长度减完后加上省略号
        current.desc = desc.substring(0, current.lh) + "...";
      } else {
        const w = desc.substr(-1, 1);
        const lastWL = this.getWL(w); //获取最后一个字符的长度
        current.ellipsisLh -= lastWL; //减去相同unicode长度的字符保证长度一致
        current.lh--; //更新当前字符串截取字符串的长度
        current.desc = desc.substring(0, current.lh); //更新内容
        this.addEllipsis(current);
      }
    },
    getWL(str) {
      //获取文字长度，英文1，中文2
      let realLength = 0,
        len = str.length,
        charCode = -1;
      for (let i = 0; i < len; i++) {
        charCode = str.charCodeAt(i);
        realLength += charCode >= 0 && charCode <= 128 ? 1 : 2;
      }
      return realLength;
    },
    formatData() {
      //格式化参数
      let stepList = this.stepList;
      stepList = stepList.map((sItem) => {
        let { list } = sItem;
        this.overVisible &&
          list.length > 0 &&
          list.push([
            {
              title: "结束",
              handlerInfo: [],
              disabled:this.overDisabled,
              last: true,
            },
          ]);
        // list = list.map((c) => {
        //   if (c.length > 0) {
        //     let headportrait = [];
        //     c.forEach((item) => {
        //       Array.isArray(item.headportrait) && headportrait.push(...item.headportrait);
        //     });
        //     c = c.map((item, index) => {
        //       item.headportraitLh = headportrait.length;
        //       item.headportrait = index === 0 ? headportrait : null;
        //     });
        //   }
        //   return c;
        // });
        return list;
      });
      this.$nextTick(() => {
        this.formatDom();
      });
    },
    showContent(item) {
      const backup = item.desc;
      item.show = !item.show;
      item.desc = item.backup;
      item.backup = backup;
    },
    imgOnError(item, index) {
      Array.isArray(item.headportrait) && item.headportrait.splice(index, 1, this.defaultImg || ImgBase64);
    },
  },
};
</script>

<style lang="scss">
@import "../src/assets/main.scss";
</style>
