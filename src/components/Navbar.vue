<template>
  <div>
    <!-- <h1>Carrepmu</h1> -->
    <div id="nav" class="nav">
      <div class="icon">
        <ul>
          <li>
            <router-link to="/"><i class="fas fa-home "></i></router-link>
          </li>
          <li v-if="$store.state.isLogin">
            <a href="#"><i class="fas fa-sign-out-alt"></i></a>
          </li>
          <li v-else-if="!$store.state.isLogin">
            <router-link to="/login"
              ><i class="fas fa-sign-in-alt"></i
            ></router-link>
          </li>
          <li>
            <router-link to="/carts"
              ><i class="fas fa-shopping-cart"></i
            ></router-link>
          </li>
        </ul>
      </div>
      <div class="text">
        <ul>
          <li><router-link to="/">Home</router-link></li>
          <li v-if="$store.state.isLogin"><a href="" @click.prevent="signOut">Sign Out</a></li>
          <li v-else-if="!$store.state.isLogin"><router-link to="/login">Sign In</router-link></li>
          <li><router-link to="/carts">View Carts</router-link></li>
        </ul>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Navbar',
  methods: {
    signOut () {
      localStorage.removeItem('access_token')
      this.$router.push({ path: '/login' })
    }
  },
  created () {
    if (localStorage.access_token) {
      this.$store.commit('setLogin', true)
    } else {
      this.$store.commit('setLogin', false)
    }
  }
}
</script>

<style lang="scss" scoped>
@import url(https://fonts.googleapis.com/css?family=Raleway:500);
body {
  width: 100%;
  margin: 0;
  padding: 0;
  overflow: hidden;
  background: rgb(0, 0, 0);
  font-family: "Raleway", sans-serif;

  & h1 {
    text-align: center;
    margin-top: 35px;
    color: rgb(255, 255, 255);
    letter-spacing: 1px;
    text-shadow: 1px 1px hsla(212, 5%, 95%, 1), -1px -1px hsla(212, 5%, 95%, 1);
  }
}

.nav {
  height: 100%;
  position: fixed;
  left: -2em;
  top: 0;
  z-index: 1000;
  transform-style: preserve-3d;
  perspective: 1000px;
}

.fas{
  color: rgb(241, 241, 241);
}
.icon {
  position: absolute;
  left: 0;
  top: 0;
  z-index: 990;
  height: 100%;
  background: rgb(15, 80, 153);

  & li {
    border-bottom: 1px solid hsla(219, 68%, 44%, 0.3);
    list-style-type: none;
  }
  & a {
    display: block;
    width: 64px;
    height: 64px;
    line-height: 64px;
    text-align: center;
    font-size: 1.6em;
    color: rgb(231, 231, 231);
    text-shadow: 0 1px 0 hsla(0, 0%, 0%, 1);
    transition: all 0.5s ease-out;

    &:hover {
      color: hsla(255, 255%, 255%, 1);
      transform: translateX(10px) scale(1.2);
    }
  }
}

.nav:hover .text {
  transform: rotateY(0deg);
}
.text {
  position: absolute;
  left: 63px;
  top: 0;
  z-index: 980;
  height: 100%;
  background:rgba(5, 64, 112, 0.856);
  border-right: 1px solid hsla(0, 6%, 7%, 0.3);
  transition: transform 0.24s linear;
  backface-visibility: hidden;
  transform-origin: left;
  transform: perspective(1000px) rotateY(90deg);

  & li {
    border-bottom: 1px solid hsla(0, 0%, 94%, 0.3);
  }
  & a {
    display: block;
    width: 200px;
    height: 64px;
    line-height: 64px;
    text-indent: 1em;
    font-size: 1.4em;
    text-decoration: none;
    color: rgb(224, 224, 224);
    text-shadow: 0 1px 0 hsla(0, 0%, 0%, 1);
    transition: all 0.5s ease;

    &:hover {
      color: hsla(255, 255%, 255%, 1);
      transform: translateX(-14px);
    }
  }
}

.nav:hover .info {
  left: 0;
  opacity: 1;
  transition: opacity 0.5s ease-in 0.1s;
}
.info {
  position: absolute;
  padding-left: 2em;
  bottom: 30px;
  z-index: 999;
  width: 264px;
  color: rgb(0, 0, 0);
  text-align: center;
  line-height: 1.6;
  opacity: 0;

  .logo p {
    width: 100px;
    height: 100px;
    margin: 0 auto;
    background: hsla(0, 0%, 15%, 1);
    color: rgb(255, 255, 255);
    opacity: 0.6;
    overflow: hidden;
    text-align: center;
    transition: all 0.5s ease;
    font-size: 2em;
    text-shadow: -1px -1px hsla(0, 0%, 31%, 1), 1px 1px hsla(0, 0%, 7%, 1);

    &:hover {
      opacity: 1;
      color: hsla(255, 255%, 255%, 1);
      text-shadow: -1px -1px hsla(0, 0%, 34%, 1), 1px 1px hsla(0, 0%, 7%, 1);
    }
  }
  .name {
    font-size: 2em;
    font-weight: bold;
    letter-spacing: 2px;
    color: hsla(0, 0%, 26%, 1);
    text-shadow: -1px -1px hsla(0, 0%, 31%, 1), 1px 1px hsla(0, 0%, 7%, 1);
  }
  .quote {
    color: rgb(255, 255, 255);
    text-shadow: 1px 1px hsla(0, 0%, 7%, 1);
  }
  .social a {
    font-size: 2em;
    color: rgb(250, 8, 8);
    letter-spacing: 0.5em;
    text-shadow: 1px 1px rgb(0, 0, 0)1px -1px hsla(0, 0%, 7%, 1);
    transition: all 0.5s ease;

    &:hover {
      color: hsla(255, 255%, 255%, 1);
      text-shadow: -1px -1px hsla(0, 0%, 34%, 1), 1px 1px hsla(0, 0%, 7%, 1);
    }
  }
}
/*
Only added a nav query for height bc width is fine
(covers full width of viewport from 270px) down to 220px.
Bottom nav info section is hidden when screen height
hits 550px or below.  Nav still functions as a fly-out
*/

@media screen and (max-height: 550px) {
  .info {
    display: none;
  }
}
@media screen and (max-width: 450px) {
  h1 {
    font-size: 7.5vw;
  }
}
</style>
