<template>
<div id="course">
  <h3>课程</h3>
  <ul>
    <li v-for="item in courseList">
      <router-link :to="{'path': '/coursedetail/' +item.id}">
        <p>{{ item.name }}</p>
      </router-link>
      <p>{{ item.brief }}</p>
      <p>级别：{{ item.level }}</p>
    </li>
  </ul>
</div>
</template>

<script>
export default {
  name: 'course',
  data () {
    return {
      courseList: []
    }
  },
  // 加载前执行的函数
  mounted: function () {
    this.initCourses()
  },
  methods: {
    initCourses(){
      let that = this;
      this.$axios.request({
        url: 'http://52.15.206.110:8080/api/courses/',
        method: 'GET'
      }).then(function (response) {
        that.courseList = response.data
      })
    }
  }
}
</script>

<style>

</style>
