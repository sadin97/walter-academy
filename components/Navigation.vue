<template>
  <header>
    <nuxt-link
      style="margin-left: 10%;"
      :to="{name: 'index'}">
      <img
        class="logo"
        src="~/static/walter-logo.png"
        alt="">
    </nuxt-link>

    <div class="mobile-navigation-bar mobile">
      <font-awesome-icon icon="bars" style="color: #fff; font-size: 30px; margin-top: 18px;" @click="showMenu = !showMenu"/>
      <div class="mobile-nav" :class="{show: showMenu}">
        <i class="el-icon-close" style="color: #fff; font-size: 20px; margin-top: 20px; left: 15px; position: absolute;" @click="showMenu = !showMenu"></i>
        <ul>
          <li>
            <a href="https://www.walter.ba"><font-awesome-icon icon="home" style="color: #fff; font-size: 20px;"/></a>
          </li>
          <li @click="showMenu = !showMenu">
            <nuxt-link :to="{ name: 'courses' }">Courses</nuxt-link>
          </li>
          <li @click="showMenu = !showMenu">
            <nuxt-link :to="{ name: 'blog' }">Blog</nuxt-link>
          </li>
          <li @click="showMenu = !showMenu">
            <a href="https://walter.ba/careers/jobs">Jobs</a>
          </li>
        </ul>
      </div>
    </div>
    <div class="navigation-bar desktop">
      <ul>
        <li>
          <a href="https://www.walter.ba"><font-awesome-icon icon="home" style="color: #fff; font-size: 20px;"/></a>
        </li>
        <li>
          <nuxt-link :to="{ name: 'courses' }">Courses</nuxt-link>
        </li>
        <li>
          <nuxt-link :to="{ name: 'blog' }">Blog</nuxt-link>
        </li>
        <li>
          <a href="https://walter.ba/careers/jobs">Jobs</a>
        </li>
      </ul>

      <div class="loginIcon">
        <span style="font-size: 16px; padding-right: 5px;">Login</span> <font-awesome-icon icon="sign-in-alt" />
      </div>
    </div>


  </header>
</template>

<script>
export default {
  data() {
    return {
      showMenu: false
    }
  }
}
</script>

<style lang="scss" scoped>
@import "../assets/variables";
@import "../assets/mixins";

.show {
  right: 0 !important;
}

.mobile-nav {
  transition: ease .3s;
  position: fixed;
  z-index: 20;
  top: 0;
  right: -100vw;
  width: 100vw;
  height: 100vh;
  background: $dark-color;

  .close {
    color: white;
    font-size: 1.6em;
    margin: 30px 0 0 30px;
  }

  ul {
    height: 80vh;
    -webkit-padding-start: 10px;
    list-style: none;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: space-around;

    li {
      a {
        font-size: 2em;
        text-decoration: none;
        color: #FFFFFF;
        margin: 1em 0.5em;
      }

      .nuxt-link-exact-active {
        color: $main-color;
      }

      .nuxt-link-active {
        color: $main-color;
      }
    }
  }
}

header {
  width: 100%;
  height: 80px;
  background-color: rgba($dark-color, 0.7);
  display: flex;
  align-items: center;
  justify-content: space-between;
  position: fixed;
  top: 0;
  left: 0;
  z-index: 10;

  .logo {
    height: 3em;
  }

  .mobile-navigation-bar {
    display: flex;
    align-items: center;
    height: 4em;
    margin-right: 10%;

    .open {
      color: white;
      font-size: 1.6em;
    }

    .dropdown-menu {
      list-style: none;
      justify-content: space-around;
      position: absolute;
      top: 60px;
      display: flex;
      flex-direction: column;

      li {
        justify-content: center;
        align-items: center;
        text-decoration: none;
        color: #FFFFFF;
        padding: 1em 1em;
        background-color: #47494e;
      }
    }
  }

  .navigation-bar {
    display: flex;
    align-items: center;
    height: 4em;
    margin-right: 10%;

    ul {
      -webkit-padding-start: 10px;
      list-style: none;
      display: flex;
      justify-content: space-around;
      margin: 0 auto ;
      /*display:table;*/
      padding: 0;

      li {

        a {
          text-decoration: none;
          color: #FFFFFF;
          padding: 2em 2em;
          @include screen-size('m') {
            padding: 1em 1em;
          }
        }

        .nuxt-link-exact-active {
          color: $main-color;
        }
        .nuxt-link-active {
          color: $main-color;
        }
      }
    }
    .dropdown-menu {
      list-style: none;
      justify-content: space-around;
      position: absolute;
      top: 80px;
      display: flex;
      flex-direction: column;

      li {
        justify-content: center;
        align-items: center;
        text-decoration: none;
        color: #FFFFFF;
        padding: 1em 1em;
        background-color: #47494e;

        @include screen-size('l') {
          padding: 0.7em 0.7em;
        }
        @include screen-size('m') {
          padding: 0.7em 0.7em;
        }
      }
    }
  }
}
.mobile {
  display: none !important;
}

@media only screen and (max-device-width : 480px) {
  .desktop {
    display: none !important;
  }

  .mobile{
    display: initial !important;
  }
}

  .loginIcon {
    color: #fff;
    font-size: 20px;
    text-align: right;
    /* float: right; */
    position: absolute;
    right: 20px;
    display: flex;
    align-items: center;
    /* padding: 0px; */
    background-color: #0094ca;
    padding: 5px;
    border-radius: 5px;
  }
  .loginIcon:hover {
    transition: 0.2s;
    cursor: pointer;
    background-color: #047da9;
  }
</style>
