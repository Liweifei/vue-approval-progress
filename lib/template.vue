<template>
  <div class="vue-approval-progress">
    <div class="stepItem" v-for="(list, lIndex) in stepList" :key="lIndex">
      <div class="itemBox" v-for="(item, index) in list" :key="index">
        <div class="iconBox">
          <template v-if="Array.isArray(item.headportrait)">
            <div
              class="imgBox"
              v-for="(imgItem, imgIndex) in item.headportrait"
              :key="imgIndex"
            >
              <img :src="imgItem" @error="imgOnError(item, imgIndex)" />
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
                : 'vapfont vap-hetong',
            ]"
          ></i>
        </div>
        <div class="r" :class="item.headportraitLh ? `r${item.headportraitLh}` : null">
          <h2 :class="{ isFinished: item.last }">{{ item.title }}</h2>
          <div
            class="userInfoBox"
            v-for="(infoItem, iIndex) in item.handlerInfo"
            :key="iIndex"
          >
            <div class="nameBox">
              <span class="roleName">{{ infoItem.post }}</span>
              <span class="name">{{ infoItem.name }}</span>
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
            <p class="main" :keyindex="lIndex + '-' + index" ref="fillText">
              {{ item.desc }}
            </p>
            <span class="showBtn" v-if="item.haveBtn" @click="showContent(item)">
              {{ item.show ? "收起" : "展开" }}
            </span>
          </div>
          <div class="markInfo" v-if="item.mark">
            <span class="msg" :style="{ color: item.markColor }">{{ item.mark }}</span>
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
      default: 2,
    },
    overVisible: {
      type: Boolean,
      default: true,
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
  },
  methods: {
    init() {
      this.stepList = JSON.parse(JSON.stringify(this.dataList));
      this.formatData();
    },
    formatDom() {
      const fliterTextDom = this.$refs.fillText;
      if (!fliterTextDom) return;
      const compareH = this.maxRow * 22;
      fliterTextDom.forEach((item) => {
        const key = item.getAttribute("keyindex").split("-");
        const io = item.scrollHeight > compareH;
        let stepList = this.stepList[key[0]][key[1]];
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
      let current = this.stepList[key[0]][key[1]];
      const compareH = this.maxRow * 22;
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
      this.overVisible &&
        stepList.length > 0 &&
        stepList.push([
          {
            title: "结束",
            handlerInfo: [],
            last: true,
          },
        ]);
      stepList = stepList.map((list) => {
        let rs = list;
        if (list.length > 1) {
          let headportrait = [];
          rs.forEach((item) => {
            Array.isArray(item.headportrait) && headportrait.push(...item.headportrait);
          });
          rs = rs.map((item, index) => {
            item.headportraitLh = headportrait.length;
            item.headportrait = index === 0 ? headportrait : null;
          });
        }
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
      Array.isArray(item.headportrait) && item.headportrait.splice(index, 1, ImgBase64);
    },
  },
};
</script>

<style lang="scss">
@import "../src/assets/main.scss";
</style>
