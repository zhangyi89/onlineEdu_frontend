<template>
  <div id="courseDetail">
    <h3>课程详情</h3>

    <ul>

      <p><strong>标题：</strong>{{ courseDeatil.name}}</p>
      <p><strong>难度：</strong>{{ courseDeatil.level }}</p>
      <p><strong>课时：</strong>{{ courseDeatil.coursedetail.hours}}</p>
      <p><strong>学习人数：</strong>{{ }}</p>
      <p><strong>评分：</strong>{{ }}</p>

      <p><strong>课程概述：</strong></p>
      <p>{{ courseDeatil.brief }}</p>

      <p><strong>课程价格：</strong></p>
      <!--课程价格列表-->
      <div>
        <li v-for="(item, $index) in courseDeatil.price_policy">{{ item }}</li>
      </div>
      <div id="pricePolicy" style="margin-top: 66px" _v-22aca6f5>
        <ul
          style="width: 1100px; height: auto; margin: 70px auto; padding: 0; display: flex; flex-wrap: wrap; justify-content: space-around"
          _v-22aca6f5=""> <!--v-for-start-->
          <li _v-22aca6f5="" class="price-wrap" v-for="(item, num) in courseDeatil.price_policy"
              v-bind:class="[{'price-wrap-active':num==selectCourseIndex}]" v-on:click="choiceCourse(num)">
            <span _v-22aca6f5="" class="price"
                  v-bind:class="[{'price-active':num==selectCourseIndex}]">¥&nbsp;{{ item.price }}</span> <span
            _v-22aca6f5="" class="limit" id="180"
            v-bind:class="[{'limit-active':num==selectCourseIndex}]">有效期{{ item.valid_period}}</span>
          </li><!--v-for-end-->
        </ul>
      </div>
      <!--购买 加入购物车-->
      <div style="justify-content: center; margin-top: 66px; text-align: center;" _v-22aca6f5="">
        <button class="charge-btn-fir charge-btn-active" style="margin-right: 48px" _v-22aca6f5="">购买</button>
        <button class="charge-btn-fir btn-back-bkg-fir" _v-22aca6f5=""><span style="padding-right: 26px" _v-22aca6f5="" @click="buyCart">加入购物车</span>
        </button>
        <div class="pur-tip-wrap" _v-22aca6f5="">
          <div class="sub-tip" _v-22aca6f5=""><img style="margin-left: 17px"
                                                   src="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAACYAAAAmCAMAAACf4xmcAAAAVFBMVEUAAACDz0t5xz94x0CA4kB4xz95yUF5xkB5x0B5x0B5x0B4xz94x0B7zEJ5xz95x0F7ykF5yEB6x0B5yEJ5xj95x0B5yUN5zkd5xkB5xz95x0B4xj+60V+RAAAAG3RSTlMAC7i/B9VH96Zp7+mMINxRKHZePcKeMRLPyoPMh/HAAAABDklEQVQ4y43T6W6EIBSG4Q8RBFncdTrn/u+zsWWqDMv0/QXJkxwlgCin1eq7XjTbfKAQmx50i8851GpDbwmZqFFQpuZttOwpmx/vSlOpfrmUpHLGITT2VEmw8I+Cqqnrw6rtp2LmE+Mnm+hjEsCDSn0Nln7aAFeexQBBZwbQNcXCUS1QFdU2YTNhraqQha+qkEJXVaEV/Ws800VFHCKsWmBI1DX0tZ1xurwiiy2sOnm6vCKNmSKXVTTioMgtOeUB8NhlFFkAM0UuqPReisixpnDLh+iOmUR14W01VO2J3w5fUw3+81AFw1+LKSqHW04UJjJEMZVB3RNJO0/OyyGX3MxlvN1RbJmsWrmyekTUN6lQaIyfaFE5AAAAAElFTkSuQmCC"
                                                   width="14" height="14" alt="" _v-22aca6f5=""> <span class="sub-text"
                                                                                                       _v-22aca6f5=""></span>
          </div>
        </div>
        <div class="pur-warn-wrap" _v-22aca6f5="">
          <div class="sub-tip" _v-22aca6f5=""><img style="margin-left: 17px"
                                                   src="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAABgAAAAYBAMAAAASWSDLAAAAIVBMVEUAAAD/qwD/qwD/rwD/rAD/qgD/qwD/qwD/qgD/qgD/qgDW3ydwAAAACnRSTlMAQPMbbNm2m07Gl35RogAAAH9JREFUGNNjAAJmtyDVFAMgA8SuWgUEyyG8plVgoAFis6yCAgcgpwtIr5wFJFYAdWgB6YVSQGKRAQP7KhhnVQGDFYKzmMELwVnCkIXgLGOIQnCWMmghOItQOCjKUAxAMRpoKdhtEEvZV8FBAcShS7zADkX2AprnEN7GDBBEUAEAh3uLdcv6paQAAAAASUVORK5CYII="
                                                   width="14" height="14" alt="" _v-22aca6f5=""> <span class="warn-text"
                                                                                                       _v-22aca6f5=""></span>
          </div>
        </div>
      </div>

      <p><strong>为什么学这门课程：</strong></p>
      <p>{{ courseDeatil.coursedetail.why_study }}</p>

      <p><strong>我将学到哪些内容？</strong></p>
      <p>{{ courseDeatil.coursedetail.what_to_study_brief}}</p>

      <p><strong>此项目如何有助于我的职业生涯？</strong></p>
      <p>{{ courseDeatil.coursedetail.career_improvement }}</p>

      <p><strong>课程先修要求</strong></p>
      <p>{{ courseDeatil.coursedetail.prerequisite }}</p>

      <p><strong>推荐课程</strong></p>
      <p>若你缺乏相关经验，建议学习以下课程</p>
      <div>
        <li style="cursor: pointer" v-for="item in courseDeatil.recommend_courses" @click="recommend_courses(item.id)">
          <strong>{{ item.id }}{{ item.name }}</strong>
        </li>
      </div>

      <p><strong>课程讲师简介</strong></p>
      <li v-for="item in courseDeatil.teachers">
        <p>{{ item.name}} {{ item.image }}{{ item.role }}
          {{ item.signature }} {{ item.brief }}</p>
      </li>

      <p><strong>常见问题</strong></p>
      <li v-for="item in courseDeatil.questions">
        <p>{{ item.question}}</p>
        <p>{{ item.answer}}</p>
      </li>
      <!--<br>-->
      <!--<div>-->
      <!--<p>价格：{{ }}</p>-->
      <!--</div>-->
      <!--<div><strong>课程章节：</strong>-->
      <!--<ul>-->
      <!--<li v-for="item in courseDeatil.course_captal"><p>{{ item }}</p></li>-->
      <!--</ul>-->
      <!--</div>-->

    </ul>
  </div>
</template>

<script>
  export default {
    data() {
      return {
        courseDeatil: [],
        courseId: this.$route.params.id,
        active: false,
        selectCourseIndex: -1,
      }
    },
    mounted: function () {
      this.initCourseDetail()
    },
    methods: {
      // 初始请求
      initCourseDetail() {
        let nid = this.courseId;
        let that = this;
        let url = 'http://52.15.206.110:80/api/coursedetail/' + nid;
        this.$axios.request({
          url: url,
          method: 'GET',
          responseType: 'json'
        }).then(function (response) {
          that.courseDeatil = response.data;
//          that.courseTitle = response.data.course
        })
      },
      // 关联课程跳转
      recommend_courses(courseId) {
//        this.$router.push({name:"courseDetail", params:{id: courseId}})
        this.$router.push('/coursedetail/' + courseId);
        // 重新发送请求
        this.courseId = courseId;
        this.initCourseDetail();
      },
      // 选择课程
      choiceCourse: function (index) {
        this.selectCourseIndex = index;
      },
      // 加入购物车
      buyCart() {
        // 首先判断用户是否登录，没有登录则跳转到登录页面
        // 获取商品信息，并把商品信息添加到redis中
        if (this.selectCourseIndex === -1){
          alert('请选择价格')
        }else{
          this.$axios.request({
            url: 'http://52.15.206.110:80/api/shopCart/',
            method: 'POST',
            data: {
              course_id: this.courseId,
              policy_id: this.courseDeatil.price_policy[this.selectCourseIndex].id,
            },
          }).then(function (response) {
            alert("添加成功")
          }).catch(function (response) {
            alert("添加购物车失败")
          });
        }

      }
    }
  }
</script>

<style>
  * {
    padding: 0;
    margin: 0;
  }

  .price-wrap[_v-22aca6f5] {
    list-style: none;
    width: 220px;
    height: 112px;
    border: 1px solid #979797;
    cursor: pointer;
    margin-right: 60px;
    margin-bottom: 60px;
  }

  .price-wrap-active[_v-22aca6f5] {
    background: #7ed321;
    border: 1px solid #7ed321;
  }

  .price[_v-22aca6f5] {
    font-size: 24px;
    letter-spacing: 1.92px;
    display: block;
    color: #333;
    margin-top: 17px;
    text-align: center;
  }

  .price[_v-22aca6f5] {
    font-size: 24px;
    letter-spacing: 1.92px;
    display: block;
    color: #333;
    margin-top: 17px;
  }

  .limit[_v-22aca6f5] {
    display: block;
    color: #9b9b9b;
    font-size: 20px;
    letter-spacing: 1.6px;
    margin-top: 9px;
    text-align: center;
  }
  .limit-active[_v-22aca6f5], .price-active[_v-22aca6f5] {
    color: #fff;
  }
  .style {
    justify-content: center;
    margin-top: 66px;
    text-align: center;
}
  .charge-btn-fir[_v-22aca6f5] {
    width: 181px;
    height: 51px;
    font-size: 14px;
    color: #fff;
    letter-spacing: 1.12px;
    text-align: center;
    background: #f5a623;
    border-radius: 82px;
}
    .charge-btn-active[_v-22aca6f5] {
    background: #7ed321;
    box-shadow: 0 2px 4px 0 #e8e8e8;
    color: #fff;
}
  button {
    cursor: pointer;
    outline: none;
}
  button, select {
    outline: none;
    border: none;
}
  button, input, select, textarea {
    font-family: inherit;
    font-size: inherit;
    line-height: inherit;
}
  button, select {
    text-transform: none;
}
  button, input, optgroup, select, textarea {
    margin: 0;
    font: inherit;
    color: inherit;
}
  .btn-back-bkg-fir[_v-22aca6f5] {
    background: #f5a623 url(data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAABMAAAASCAMAAACO0hVbAAAAk1BMV…bQgRrHy70cL0KmrWWKTZMaNpAwFGD5cyeMwMZEt77MlPf3D5oaCoBY3zv0AAAAAElFTkSuQmCC) no-repeat 125px 15px!important;
}
  .pur-tip-wrap[_v-22aca6f5], .pur-warn-wrap[_v-22aca6f5] {
    min-width: 236px;
    height: 34px;
    background: #fff;
    box-shadow: 0 2px 8px 0 rgba(0,0,0,.2);
    border-radius: 4px;
    position: absolute;
    left: 50%;
    margin-top: -41px;
    margin-left: 265px;
    display: none;
}
</style>
