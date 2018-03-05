<template>
  <div id="app">
    <div class="nav">
      <div class="maneList">
      <ul>
        <li>
          <router-link to="/index">首页</router-link>
          <router-link to="/courses">课程</router-link>
          <router-link to="/micro">学位</router-link>
          <router-link to="/news">深科技</router-link>
        </li>
      </ul>
        </div>
      <div class="navRight">
      <ul class="login">
        <li>
          <router-link to="/login">登录</router-link>
        </li>
      </ul>
      <router-link to="/shopCart">
      <div class="nav_shopp" _v-319a3b1b=""><img
        src="data:image/svg+xml;base64,PD94bWwgdmVyc2lvbj0iMS4wIiBzdGFuZGFsb25lPSJubyI/PjwhRE9DVFlQRSBzdmcgUFVCTElDICItLy9XM0MvL0RURCBTVkcgMS4xLy9FTiIgImh0dHA6Ly93d3cudzMub3JnL0dyYXBoaWNzL1NWRy8xLjEvRFREL3N2ZzExLmR0ZCI+PHN2ZyBjbGFzcz0iaWNvbiIgd2lkdGg9IjIwMHB4IiBoZWlnaHQ9IjIwMC4wMHB4IiB2aWV3Qm94PSIwIDAgMTAyNCAxMDI0IiB2ZXJzaW9uPSIxLjEiIHhtbG5zPSJodHRwOi8vd3d3LnczLm9yZy8yMDAwL3N2ZyI+PHBhdGggZD0iTTM1Ny40NCA3NjYuNHExOC4yNCAwIDM0LjU2IDYuNzJ0MjguOCAxOC43MiAxOS4yIDI4LjMyIDYuNzIgMzQuNTYtNi43MiAzNC41Ni0xOS4yIDI4LjMyLTI4LjggMTkuMi0zNC41NiA3LjJxLTE5LjIgMC0zNS4wNC03LjJ0LTI4LjMyLTE5LjItMTkuMi0yOC4zMi02LjcyLTM0LjU2IDYuNzItMzQuNTYgMTkuMi0yOC4zMiAyOC4zMi0xOC43MiAzNS4wNC02Ljcyek03NTYuOCA3NjguMzJxMTguMjQgMCAzNS4wNCA2LjcydDI4LjggMTguNzIgMTkuMiAyOC4zMiA3LjIgMzQuNTYtNy4yIDM0LjU2LTE5LjIgMjguMzItMjguOCAxOS4yLTM1LjA0IDcuMi0zNC41Ni03LjItMjguMzItMTkuMi0xOS4yLTI4LjMyLTcuMi0zNC41NiA3LjItMzQuNTYgMTkuMi0yOC4zMiAyOC4zMi0xOC43MiAzNC41Ni02Ljcyek05MTguMDggMjIzLjA0cTI2Ljg4IDAgNDEuNzYgNy4ydDIxLjEyIDE3Ljc2IDUuNzYgMjIuNTYtMy4zNiAyMC42NC0xMiAzNS41Mi0yMC42NCA1OS4wNC0yMi41NiA2My44NC0xNi44IDQ5LjkycS0xMi40OCAzOC40LTMxLjY4IDUzLjI4dC00Ny4wNCAxNC44OGwtMzIuNjQgMC02Mi40IDAtODEuNiAwLTg5LjI4IDAtMjM4LjA4IDAgMTQuNCA4Ni40IDQ4My44NCAwcTQ2LjA4IDAgNDYuMDggMzkuMzYgMCAxOS4yLTkuMTIgMzMuMTJ0LTM2IDEzLjkybC00Ni4wOCAwLTg5LjI4IDAtMTEwLjQgMC0xMTIuMzIgMC05Mi4xNiAwLTUyLjggMHEtMTkuMiAwLTMyLjE2LTguNjR0LTIxLjYtMjIuNTYtMTMuOTItMzAuMjQtOC4xNi0zMC43MnEtMC45Ni01Ljc2LTUuMjgtMjcuODR0LTEwLjU2LTU1LjItMTMuOTItNzMuOTItMTUuMzYtODIuMDhxLTE4LjI0LTk2Ljk2LTQxLjI4LTIxNmwtNzIgMHEtMTQuNCAwLTI0LTcuMnQtMTUuODQtMTcuMjgtOC42NC0yMS42LTIuNC0yMS4xMnEwLTE5LjIgMTIuOTYtMzEuNjh0MzUuMDQtMTIuNDhsMjEuMTIgMCAxOS4yIDAgMjQgMCAzMi42NCAwcTE5LjIgMCAzMC43MiA1Ljc2dDE4LjI0IDE0LjQgOS42IDE4LjI0IDQuOCAxNi4zMnExLjkyIDcuNjggMy44NCAyMS42dDMuODQgMjguMzJxMi44OCAxNy4yOCA1Ljc2IDM2LjQ4bDY1Ni42NCAweiIgZmlsbD0iIzk5OTk5OSIgLz48L3N2Zz4="
        alt="" _v-319a3b1b="" style=""> <img
        src="data:image/svg+xml;base64,PD94bWwgdmVyc2lvbj0iMS4wIiBzdGFuZGFsb25lPSJubyI/PjwhRE9DVFlQRSBzdmcgUFVCTElDICItLy9XM0MvL0RURCBTVkcgMS4xLy9FTiIgImh0dHA6Ly93d3cudzMub3JnL0dyYXBoaWNzL1NWRy8xLjEvRFREL3N2ZzExLmR0ZCI+PHN2ZyBjbGFzcz0iaWNvbiIgd2lkdGg9IjIwMHB4IiBoZWlnaHQ9IjIwMC4wMHB4IiB2aWV3Qm94PSIwIDAgMTAyNCAxMDI0IiB2ZXJzaW9uPSIxLjEiIHhtbG5zPSJodHRwOi8vd3d3LnczLm9yZy8yMDAwL3N2ZyI+PHBhdGggZD0iTTM1Ny40NCA3NjYuNHExOC4yNCAwIDM0LjU2IDYuNzJ0MjguOCAxOC43MiAxOS4yIDI4LjMyIDYuNzIgMzQuNTYtNi43MiAzNC41Ni0xOS4yIDI4LjMyLTI4LjggMTkuMi0zNC41NiA3LjJxLTE5LjIgMC0zNS4wNC03LjJ0LTI4LjMyLTE5LjItMTkuMi0yOC4zMi02LjcyLTM0LjU2IDYuNzItMzQuNTYgMTkuMi0yOC4zMiAyOC4zMi0xOC43MiAzNS4wNC02Ljcyek03NTYuOCA3NjguMzJxMTguMjQgMCAzNS4wNCA2LjcydDI4LjggMTguNzIgMTkuMiAyOC4zMiA3LjIgMzQuNTYtNy4yIDM0LjU2LTE5LjIgMjguMzItMjguOCAxOS4yLTM1LjA0IDcuMi0zNC41Ni03LjItMjguMzItMTkuMi0xOS4yLTI4LjMyLTcuMi0zNC41NiA3LjItMzQuNTYgMTkuMi0yOC4zMiAyOC4zMi0xOC43MiAzNC41Ni02Ljcyek05MTguMDggMjIzLjA0cTI2Ljg4IDAgNDEuNzYgNy4ydDIxLjEyIDE3Ljc2IDUuNzYgMjIuNTYtMy4zNiAyMC42NC0xMiAzNS41Mi0yMC42NCA1OS4wNC0yMi41NiA2My44NC0xNi44IDQ5LjkycS0xMi40OCAzOC40LTMxLjY4IDUzLjI4dC00Ny4wNCAxNC44OGwtMzIuNjQgMC02Mi40IDAtODEuNiAwLTg5LjI4IDAtMjM4LjA4IDAgMTQuNCA4Ni40IDQ4My44NCAwcTQ2LjA4IDAgNDYuMDggMzkuMzYgMCAxOS4yLTkuMTIgMzMuMTJ0LTM2IDEzLjkybC00Ni4wOCAwLTg5LjI4IDAtMTEwLjQgMC0xMTIuMzIgMC05Mi4xNiAwLTUyLjggMHEtMTkuMiAwLTMyLjE2LTguNjR0LTIxLjYtMjIuNTYtMTMuOTItMzAuMjQtOC4xNi0zMC43MnEtMC45Ni01Ljc2LTUuMjgtMjcuODR0LTEwLjU2LTU1LjItMTMuOTItNzMuOTItMTUuMzYtODIuMDhxLTE4LjI0LTk2Ljk2LTQxLjI4LTIxNmwtNzIgMHEtMTQuNCAwLTI0LTcuMnQtMTUuODQtMTcuMjgtOC42NC0yMS42LTIuNC0yMS4xMnEwLTE5LjIgMTIuOTYtMzEuNjh0MzUuMDQtMTIuNDhsMjEuMTIgMCAxOS4yIDAgMjQgMCAzMi42NCAwcTE5LjIgMCAzMC43MiA1Ljc2dDE4LjI0IDE0LjQgOS42IDE4LjI0IDQuOCAxNi4zMnExLjkyIDcuNjggMy44NCAyMS42dDMuODQgMjguMzJxMi44OCAxNy4yOCA1Ljc2IDM2LjQ4bDY1Ni42NCAweiIgZmlsbD0iIzJjMmMyYyIgLz48L3N2Zz4="
        alt="" _v-319a3b1b="" style="display: none;"> <!--v-if--> <!--v-if--> <p _v-319a3b1b="" style="display: none;">
        点击可到您的购物车</p></div></router-link>
    </div>
      </div>
    <div>
      <router-view/>
    </div>
    <!--<h1>{{msg}}</h1>-->
    <!--<input type="button" value="点击翻转" @click="change">-->
  </div>
</template>

<script>
  export default {
    name: 'app',
    data() {
      return {
        msg: 'Welcome to Your Vue.js App'
      }
    },
    methods: {
      change() {
        let str = this.msg;
        str = str.split('').reverse().join();
        this.msg = str
      }
    }
  }
</script>

<style>
  #app {
    font-family: 'Avenir', Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    /*text-align: center;*/
    color: #2c3e50;
    margin-top: 60px;
  }

  h1, h2 {
    font-weight: normal;
  }

  ul {
    list-style-type: none;
    padding: 0;
  }

  li {
    display: inline-block;
    margin: 0 10px;
  }

  a {
    color: #42b983;
  }
  img {
    width: 30px;
    height: 30px;
    /*float: left;*/
    margin-left: 1000px;
  }
  .maneList {
    float: left;
  }
  .navRight {
    float: right;
  }

</style>
