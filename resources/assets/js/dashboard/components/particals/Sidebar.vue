<template>
  <div id="sidebar-wrapper">
    <ul class="sidebar-nav">
      <div class="user">
        <div class="avatar">
          <img class="img-fluid rounded-circle" :src="user.avatar">
        </div>
        <div class="nickname">
          <p>{{ user.name }}</p>
          <p>{{ user.email }}</p>
        </div>
        <div class="buttons">
          <a href="/"><i class="fas fa-home"></i></a>
          <a :href="userInfo"><i class="fas fa-user"></i></a>
          <a href="/setting"><i class="fas fa-cog"></i></a>
        </div>
      </div>
      <li v-for="menu in menus">
        <router-link :to="menu.uri">
          <i :class="menu.icon"></i> {{ $t(menu.label) }}
        </router-link>
      </li>
    </ul>
  </div>
</template>

<script>
  import menus from 'dashboard/config/menu'

  export default {
    data () {
      return {
        menus: menus,
        user: {}
      }
    },
    mounted() {
      this.user = window.User
    },
    computed: {
      userInfo() {
        return '/user/' + this.user.name
      }
    }
  }
</script>

<style lang="scss" scoped>
.sidebar-nav {
  position: absolute;
  top: 0;
  width: 250px;
  margin: 0;
  padding: 0;
  list-style: none;

  i {
    font-size: .9rem;
  }
}

.sidebar-nav li {
  text-indent: 20px;
  line-height: 40px;

  i {
    font-size: .6rem;
  }
}

.navbar {
  margin-bottom: 0;
}

.sidebar-nav li .user {
  display: block;
  text-align: center;
  width: 100%;
  background-color: #3d4e60;
  padding-top: 20px;
  padding-bottom: 10px;
  color: #fff;
}

.user {
  text-align: center;
  padding-top: 15px;
  background-color: #52697f;
}

.user .avatar {
  width: 80px;
  margin: 10px auto;
}

.nickname {
  color: #fff;
}

.buttons {
  height: 50px;
}
.buttons a {
  display: inline-block;
  font-size: 20px;
  width: 40px;
  height: 40px;
  line-height: 40px;
  margin-right: 5px;
  color: #828a9a;
}
.buttons a:hover {
  color: #fff;
}
.sidebar-nav li a {
  display: block;
  text-decoration: none;
  color: #999999;
}

.sidebar-nav li a:hover {
  text-decoration: none;
  color: #fff;
  background: rgba(255,255,255,0.2);
}

.sidebar-nav li .active {
  color: #fff !important;
}

.sidebar-nav li a i {
  padding-right: 10px;
}

.sidebar-nav li a:active,
.sidebar-nav li a:focus {
  text-decoration: none;
}

.active {
  background-color: #3d4e60;
  border-right: 4px solid #647f9d;
}
.active a {
  color: #fff !important;
}

.sidebar-nav > .sidebar-brand {
  height: 65px;
  font-size: 18px;
  line-height: 60px;
}

.sidebar-nav > .sidebar-brand a {
  color: #999999;
}

.sidebar-nav > .sidebar-brand a:hover {
  color: #fff;
  background: none;
}
</style>
