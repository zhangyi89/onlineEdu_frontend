<template>
  <div id="shopCart">
    <h3>购物车</h3>

    <p><strong>我的购物车（共多少门课程）</strong></p>
    <div>
      <li><strong>课程</strong>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
        <strong>有效期</strong>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
        <strong>单价</strong>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
        <strong>操作</strong></li>
    </div>
    <li v-for="(item,cid) in shopCartDetail">
      <input class="check J-check-btn" type="checkbox" _v-6651a526="">
      <span>{{ item.title }}</span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
      <select name="" id="">
        <option value="" v-for="i in item.price_policy_list">有效期{{i.valid_period}}</option>
      </select>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
      <span>{{ item.default_policy_id }}</span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
      <span><button @click="deleteCourse(cid)">删除</button></span></li>
    <ul style="width: 100%; height: 40px; background: #F7F7F7; margin: 40px 0 20px; display: flex; align-items: center">
      <li class="charge-list">
        <input class="select_all" type="checkbox">
        <span class="shopping-cart-bot-font" style="margin-left: 15px; cursor: pointer">全选</span>
      </li>
      <li class="charge-list" style="margin-left: 58px">
        <span class="shopping-cart-bot-font" style="margin-left: 15px; cursor: pointer">删除</span>
      </li>
      <li class="charge-list" style="margin-left: auto">
        <span class="shopping-cart-bot-font" style="margin-right: 62px">总计：¥0</span>
        <button class="go-charge-btn" @click="goCharge(chargeId)">去结算</button>
      </li>
    </ul>

    <h3>立即支付</h3>

    <ul class="purchase-head-wrap">
      <li class="purchase-item1">课程</li>
      <li class="purchase-item2" style="margin-left: 100px">有效期</li>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
      <li class="purchase-item3">原价</li>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
      <li class="purchase-item4">优惠券</li>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
      <li class="purchase-item5" style="margin-left: 100px">折后价</li>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
    </ul>

    <div class="project" v-for="item in courses">
      <!--<img width="170" height="115" alt="">-->
      <span class="product-fonts product-list">{{ item.title }}</span>
      <!--<span class="product-fonts product-list" >{{ item.img }}</span>-->
      <span v-for="(i,key) in item.price_policy_list">
        <span v-if="item.default_policy_id == key">
          <span id="90" style="margin-left: 90px">{{ i.valid_period}}</span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
          <span>¥{{ i.price }}</span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
        </span>
      </span>
      <span>
        <select class="coupon-select" name="coupon">
          <option v-for="itemCoupons in chargeData.coupons">
            <p value="" v-if="itemCoupons.object_id == item.id">{{itemCoupons.coupon}}</p>
          </option>
        </select>
      </span>
      <span class="product-fonts" style="margin-left: 80px">折后价</span>
    </div>
    <div>
      <h3 style="margin-top: 40px">通用优惠券</h3>
      <span>
        <select class="coupon-select" name="coupon">
          <option v-for="itemCoupons in chargeData.coupons">
            <p value="" v-if="itemCoupons.object_id == NONE">{{itemCoupons.coupon}}</p>
          </option>
        </select>
      </span>
    </div>
    <div style="margin-left: 1100px; margin-bottom: 40px">
      <span><strong>我的贝里</strong></span>
      <span style="font-size: 30px">¥{{ chargeData.balance }}</span>
    </div>

    <div>
      <span><strong>支付方式：</strong></span>
      <span>支付宝</span>
      <span style="margin-left: 800px">应付款</span><span style="font-size: 30px">¥888888</span>
      <button class="go-buy-btn" @click="payNow()">立即支付</button>
    </div>


  </div>
</template>


<script>
  export default {
    data() {
      return {
        shopCartDetail: [],
        shooenPricePolicy: "",
        chargeId: 1,
        chargeData: [],
        courses: [],
      }
    },
    mounted: function () {
      this.initShopCartDetail()
    },
    methods: {
      initShopCartDetail() {
        let that = this;
        let url = 'http://52.15.206.110:80/api/shopCart/';
        this.$axios.request({
          url: url,
          method: "GET",
          responseType: "json",
        }).then(function (response) {
          that.shopCartDetail = response.data;
          console.log(response.data);
        }).catch(function (response) {
          alert("错误")
        })
      },
      deleteCourse(cid) {
        let that = this;
        let url = 'http://52.15.206.110:80/api/shopCart/';
        this.$axios.request({
          url: url,
          method: "DELETE",
          data: {
            cid: cid,
          }
        }).then(function (response) {
          alert("删除成功")
        })
      },
      goCharge(chargeId) {
        let that = this;
        let url = 'http://127.0.0.1:8000/api/charge/';
        this.$axios.request({
          url: url,
          method: "POST",
          responseType: "json",
          data: {
            chargeId: chargeId,
          }
        }).then(function (response) {
          console.log(response.data);
          that.chargeData = response.data;
          that.courses = response.data.courses;
          alert("去结算成功")
        }).catch(function (response) {
          alert("添加失败")
        })
      },
      payNow() {
        let that = this;
        let url = 'http://52.15.206.110:80/api/pay/';
        this.$axios.request({
          url: url,
          method: "POST",
          responseType: "json",
          data: {
            "courses": [{"courseID": 1, "coursePrice": 199, "valid_period":"30", "coupon": "满10元减100"}],
            "commCoupon": "100元优惠卷",
            "beili": 100,
            "payWay": "1",
          }
        }).then(function (response) {
          console.log(response.data);
          alert("生成订单成功")
        }).catch(function (response) {
          alert("生成支付订单失败")
        })

      }
    }
  }
</script>


<style>
  * {
    padding: 0;
    margin: 0;
  }

  body {
    font-family: "Helvetica Neue", Helvetica, Arial, sans-serif;
    font-size: 14px;
    line-height: 1.42857143;
    color: #333;
    background-color: #fff;
  }

  input[type=checkbox], input[type=radio] {
    margin: 4px 0 0;
    margin-top: 1px \9;
    line-height: normal;
    box-sizing: border-box;
    padding: 0;
    font-family: inherit;
    font-size: inherit;
  }

  input[type="radio" ], input[type="checkbox" ] {
    background-color: initial;
    cursor: default;
    margin: 3px 0.5ex;
    padding: initial;
    border: initial;
  }

  input, textarea, select, button {
    text-rendering: auto;
    color: initial;
    letter-spacing: normal;
    word-spacing: normal;
    text-transform: none;
    text-indent: 0px;
    text-shadow: none;
    display: inline-block;
    text-align: start;
    margin: 0em;
    font: 400 11px system-ui;
  }

  button {
    cursor: pointer;
    font-family: inherit;
  }

  .project[_v-dcd4ed56] {
    height: 220px;
    display: -webkit-box;
    display: -ms-flexbox;
    display: flex;
    -webkit-box-align: center;
    -ms-flex-align: center;
    align-items: center;
    border-bottom: 1px solid #e8e8e8;
    position: relative;
  }

  .project div {
    position: absolute;
    left: 31px;
    top: 50px;
  }

  .go-buy-btn {
    width: 160px;
    height: 80px;
    background: #78c63f;
    outline: none;
    border: none;
    color: #fff;
    font-size: 18px;
    line-height: 80px;
    text-align: center;
  }

</style>
