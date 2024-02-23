<template>
  <div class="home">
    <van-sticky>
      <!-- 通知信息 -->
      <div class="display background-fff">
        <van-notice-bar
          left-icon="volume-o"
          color="#1989fa"
          background="#ecf9ff"
          text="Online and offline stores applet-0.0.1"
          style="width: 80%"
        />
        <div class="shareBtn" @click="showShare = true" style="width: 15%; margin-left: auto"></div>
        <!-- <van-cell
          style="width: 15%; margin-left: auto"
          title="分享"
          @click="showShare = true"
        /> -->
      </div>
      <!-- 轮播图 -->
      <van-swipe class="my-swipe" :autoplay="2000" indicator-color="white">
        <van-swipe-item v-for="item in swipeData" :key="item.key">
          {{ item.name }}
        </van-swipe-item>
      </van-swipe>
      <!-- 切换服装种类按钮 -->
      <div class="display padding-top16 background-fff">
        <van-button
          style="width: 20%"
          size="small"
          v-for="item in clothType"
          :key="item.key"
          :type="item.key === activeComponent ? 'info' : 'default'"
          @click="selectChange(item)"
          >{{ item.name }}</van-button
        >
      </div>
    </van-sticky>
    <!-- 各种服装组件 -->
    <component :is="activeComponent"></component>
    <!-- 购物车 -->
    <van-goods-action v-if="false">
      <van-goods-action-icon icon="chat-o" text="客服" @click="onClickIcon" />
      <van-goods-action-icon icon="cart-o" text="购物车" @click="onClickIcon" />
      <van-goods-action-icon icon="shop-o" text="店铺" @click="onClickIcon" />
      <van-goods-action-button type="warning" text="加入购物车" />
      <van-goods-action-button type="danger" text="立即购买" />
    </van-goods-action>
    <!-- 分享面板 -->
    <van-share-sheet
      v-model="showShare"
      title="立即分享给好友"
      :options="options"
      @select="onSelect"
    />
  </div>
</template>

<script>
// @ is an alias to /src
import tShirt from "@/components/tShirt.vue";
import coat from "@/components/coat.vue";
import jeans from "@/components/jeans.vue";
import hoody from "@/components/hoody.vue";
import downJacket from "@/components/downJacket.vue";
import sportPant from "@/components/sportPant.vue";

export default {
  name: "HomeView",
  data() {
    return {
      showShare: false,
      activeComponent: "tShirt",
      options: [
        { name: "微信", icon: "wechat" },
        { name: "微博", icon: "weibo" },
        { name: "复制链接", icon: "link" },
        { name: "分享海报", icon: "poster" },
        { name: "二维码", icon: "qrcode" },
      ],
      swipeData: [
        { name: "T恤衫", key: "tShirt" },
        { name: "外套", key: "coat" },
        { name: "牛仔裤", key: "jeans" },
        { name: "羽绒服", key: "downJacket" },
        { name: "卫衣", key: "hoody" },
      ],
      clothType: [
        { name: "T恤衫", key: "tShirt" },
        { name: "外套", key: "coat" },
        { name: "牛仔裤", key: "jeans" },
        { name: "羽绒服", key: "downJacket" },
        { name: "卫衣", key: "hoody" },
      ],
    };
  },
  components: {
    tShirt,
    coat,
    jeans,
    hoody,
    downJacket,
    sportPant,
  },
  methods: {
    selectChange(item) {
      this.activeComponent = item.key;
      console.log(item.key);
      console.log("selectChange");
    },
    onSelect(option) {
      this.showShare = false;
    },
    onClickButton() {},
    onClickIcon() {},
  },
};
</script>
