<template>
  <div class="navbar">
    <img class='logo' src="https://upload.wikimedia.org/wikipedia/commons/thumb/0/08/Netflix_2015_logo.svg/1920px-Netflix_2015_logo.svg.png" alt="Netflix Logo"/>
    <div class='nav-div'>
        <ul class='nav-list'>
          <router-link to="/"><li class='nav-item'><span class="active" >Home</span></li></router-link>
          <router-link to="/movies"><li class='nav-item'><span >Movies</span></li></router-link>
          <router-link to=""><li class='nav-item'><span >Tv Shows</span></li></router-link>
          <router-link to=""><li class='nav-item'><span >Recently Added</span></li></router-link>
          <router-link to=""><li class='nav-item'><span >My List</span></li></router-link>
        </ul>
    </div>
    <img class='avatar' src="https://i.pinimg.com/originals/0d/dc/ca/0ddccae723d85a703b798a5e682c23c1.png" alt="Avatar" />
  </div>
</template>

<script>
export default {
  name: 'Navbar',
  data () {
    return {
    }
  }
}
</script>

<style scoped>
  .logo-div{
      float: left;
  }
  .nav-div{
      margin-left: 100px;
      position: absolute;
      top: 15px;
      left: 40px;
  }
  .navbar {
      position: relative;
      top: 0;
      height: 30px;
      padding: 20px;
      background-color: #111;
      display: flex;
      justify-content: space-between;
  }

  .logo {
      width: 80px;
      left: 20px;
      height: 20px;
      position: sticky;
  }
  .avatar {
      position: fixed;
      width: 30px;
      right: 20px;
      top: 15px;
      border-radius: 2px;
  }
  .nav-list {
      list-style-type: none;
      /* margin-left: 100px; */
    /*  position: fixed;
      top: 15px; */
      vertical-align: middle;
      float: left;
      padding: 0;
      overflow: hidden;
      /* background-color: #333; */
  }
  .nav-item {
      float: left;
  }
  .nav-item span {
      display: block;
      color: rgb(238, 238, 238);
      text-align: center;
      padding: 4px 16px;
      text-decoration: none;
      cursor: pointer;
  }
  .nav-item span:hover {
      background-color: rgb(36, 36, 36);
      border-radius: 5px;
  }
</style>
