<template>
  <header>
    <nav>
      <div id="mySidemenu" class="sidemenu">
        <a href="javascript:void(0)" class="close" @click="closeSM">&times;</a>
        <div class="sm-wrapper">
          <div class="dropdown">
            <a class="title" href="#" @click="openSubMenu('dropdown-content1')">Section 1</a>
            <div class="dropdown-content" id="dropdown-content1">
              <ul style="list-style-type: none; padding: 0;">
                <li><router-link to="/unit1">Unit 1. Bonding, Introduction to Structural Representations</router-link></li>
                <li><router-link to="/unit2">Unit 2. More Structural Representations and Isomers</router-link></li>
                <li><router-link to="/unit3">Unit 3. </router-link></li>
                <li><router-link to="/unit4">Unit 4. </router-link></li>
                <li><router-link to="/">Unit 5. </router-link></li>
                <li><router-link to="/">Unit 6. </router-link></li>
                <li><router-link to="/">Unit 7. </router-link></li>
                <li><router-link to="/">Unit 8. </router-link></li>
                <li><router-link to="/">Unit 9. </router-link></li>
                <li><router-link to="/">Unit 10. </router-link></li>
              </ul>
            </div>
          </div>
          <div class="dropdown">
            <a class="title" href="#" @click="openSubMenu('dropdown-content2')">Section 2</a>
            <div class="dropdown-content" id="dropdown-content2">
              <ul style="list-style-type: none; padding: 0;">
                <li><router-link to="/scroll">Unit 11.</router-link></li>
                <li><router-link to="/scroll">Unit 12. </router-link></li>
                <li><router-link to="/scroll">Unit 13. </router-link></li>
              </ul>
            </div>
          </div>
          <a class="title" href="#">Section 3</a>
        </div>
      </div>
      <div id="pg-content">
        <div class="open" @click="openSM">&#9776;</div>
      </div>
      <h3><router-link to="/" style="text-decoration: none; font-family: 'League Spartan', sans-serif;">Organic Chemistry E-Text</router-link></h3>
    </nav>
  </header>

  <div @click="clickOut">
    <router-view/> 
  </div>
</template>

<script>
import { RouterLink, RouterView } from 'vue-router';

export default{
  components:{
    RouterLink,
    RouterView
  },

  methods: {
    openSM(){
      if ((parseInt( document.getElementById("mySidemenu").style.width) == 450)|| (parseInt(document.getElementById("mySidemenu").style.width) == 350)) {
        this.closeSM();
      }
      else {
        if (window.screen.width <=725) {
          document.getElementById("mySidemenu").style.width ="350px";
          document.getElementById("pg-content").style.marginLeft = "0px";
        }
        else {
          document.getElementById("mySidemenu").style.width ="450px";
          document.getElementById("pg-content").style.marginLeft = "450px";
        }
      }
    },

    clickOut(){
      if ((parseInt(document.getElementById("mySidemenu").style.width) == 450) || (parseInt(document.getElementById("mySidemenu").style.width) == 350)) {
        this.closeSM();
      }
    },
    
    closeSM(){
      document.getElementById("mySidemenu").style.width = "0";
      document.getElementById("pg-content").style.marginLeft ="0";
    },

    openSubMenu(id){
      const el = document.getElementById(id);
      if (window.getComputedStyle(el).display == "block") {
        el.style.display = "none";
      }
      else {
        el.style.display = "block";
      }
    },
  },
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  background-color: rgb(72, 72, 72);
  overflow: hidden;
  max-width: 100%;
}

header{
  background-color: rgb(255, 255, 130);
}

nav{
  margin-left:5%;
  display: flex;
}

nav a {
  font-weight: bold;
  color: #2c3e50;
}

nav a.router-link-exact-active {
  color: #42b983;
}

/* RouterLink */
.overlay{
  position:fixed;
  background-color: rgba(67, 67, 67, 0.6);
  width:100%;
  height:100%;
  color:white;
  cursor: pointer;
  display:none;
}

h3 {
  margin: 3vw;
  font-size: 200% !important;
}

.open {
  margin: 0%;
  font-size:2vw;
  cursor:pointer;
  color:#5b5b5b
}

nav {
  display: flex;
  align-items: center;
  margin-left: 3vw !important;
}
/* SIDE MENU PART */
 
.sm-wrapper{
  display: flex;
  flex-direction: column;
  align-items: flex-start;
}
 
.sidemenu{
  display: flex;
  text-wrap:nowrap;
  overflow-y: scroll;
  overflow-x: hidden;
  height: 100%;
  width: 0;
  position: fixed;
  z-index: 1;
  top: 0;
  left: 0;
  background-color: rgb(72, 72, 72);
  transition: 0.5s;
  padding-top: 10px;
  -ms-overflow-style: none;  /* Hide scrollbar for IE and Edge */
  scrollbar-width: none;  /* Hide scrollbar for Firefox */
}

/* Hide scrollbar for IE, Edge and Firefox */
.sidemenu::-webkit-scrollbar {
  display: none;
}

.sidemenu a{
  margin:15px 20px;
  text-decoration: none;
  font-size: 15px;
  font-family: "League Spartan", sans-serif;
  color: #ffffff;
  display: block;
  margin-bottom: 20px;
  transition: 0.3s;
  }
 
.sidemenu .close{
  position: absolute;
  top: 0;
  right: 25px;
  font-size: 20px;
  margin-left: 50px;
}
 
  /* SIDE MENU HOVER EFFECT */
 
.sm-wrapper a:after{
  z-index: -1;
  position: absolute;
  left: 0%;
  width: 0;
  height: 20px;
  background: #e85e4f;
  content: '';
  transition: width 0.35s ease-in-out;
}
 
.sm-wrapper a:hover:after{
  width: 3%;
}
 
.sm-wrapper a:hover{
  padding-left: 5px;
  transition: 0.35s ease-in-out;
}

.dropdown-content {
  width: 50px;
  display: none;
  color: white;
  font-family: "League Spartan", sans-serif;
  font-size: 11px;
}


.title {
  display: flex; 
  min-width: 400px; 
  justify-content: center;
}
 
#pg-content{
  transition: margin-left 0.5s;
  padding: 5px;
}

@media screen and (max-width: 600px) {
  h3 {
    margin: 5vw;
    font-size: 6vw !important;
  }
  .open {
    font-size: 3vw !important;
  }

  .title {
    min-width: 300px;
  }
}

@media screen and (min-width: 1200px) {
  h3 {

    font-size: 2vw !important;
  }
}
</style>
