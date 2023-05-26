<template>
    <div class="text-xs">
      <div class="adminpage">
        <div class="sidebar">
            <div class="adm-select">
              <img :src="require('@/assets/ijazah.svg')" alt="">
              <p>Dashboard</p>
            </div>
            <router-link to="/" class="logoutbtn">
              <img :src="require('@/assets/terminal.svg')" alt="">
              Logout
            </router-link>
        </div>
        <div class="admincontent">
          <div class="topside">
            <div class="showregist activereg">
              <div>
                <img :src="require('@/assets/Photo.svg')" alt="">
                <p>Active</p>
              </div>
              <p>10</p>
            </div>
            <div class="showregist waitingreg">
              <div>
                <img :src="require('@/assets/Photo.svg')" alt="">
                <p>Waiting Approval</p>
              </div>
              <p>3</p>
            </div>
          </div>
          <div class="usertable">
            <div class="headusertable userdetailheadcont">
              <p class="number">no</p>
              <p>photo</p>
              <p>name</p>
              <p>action</p>
            </div>
            <div class="userlist">
              <div class="user1" v-for="n in 4">
                <div class="number">1</div>
                <router-link class="userdivs" to="/admin/[id]"><img :src="require('@/assets/1.jpg')" alt="" class="profilepic"></router-link>
                <router-link class="userdivs" to="/admin/[id]">John Doe</router-link>
                <div class="approvalcont">
                  <button class="approvalbtns">Approve</button>
                  <button class="approvalbtns reject">Reject</button>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    
  }
  </script>
  