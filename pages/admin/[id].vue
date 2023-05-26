<template>
  <div class="text-xs">
    <div class="adminpage">
      <div class="sidebar">
          <router-link to="/admin" class="adm-select">
            <img :src="require('@/assets/ijazah.svg')" alt="">
            <p>Dashboard</p>
          </router-link>
          <router-link to="/" class="logoutbtn">
            <img :src="require('@/assets/terminal.svg')" alt="">
            Logout
          </router-link>
      </div>
      <div class="admincontent">
        <router-link to="/admin" class="backbtn">
          Back
        </router-link>
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
        <div class="usertable detailtable">
          <div class="userdetailheadcont">
            Member Profile
          </div>
          <div class="profilepicdetailcontainer">
            <img class="profilepicdetail" :src="require('@/assets/1.jpg')" alt="">
          </div>
          <div>
              <div class="inputcont">
                  <div class="label" for="">Name</div>
                  <input tabindex="-1" class="inputtext registinput detailuser" type="text" name="" id="" placeholder="John Carter">
              </div>
              <div class="inputcont second">
                  <div class="label" for="">Email</div>
                  <input tabindex="-1" class="inputtext registinput detailuser" type="email" name="" id="" placeholder="Email Address">
              </div>
          </div>
          <div>
              <div class="inputcont">
                  <div class="label" for="">Phone Number</div>
                  <input tabindex="-1" class="inputtext registinput detailuser" type="tel" name="" id="" placeholder="0888-456-7890">
              </div>
              <div class="inputcont second">
                  <div class="label" for="">University</div>
                  <input tabindex="-1" class="inputtext registinput detailuser" type="text" name="" id="" placeholder="University Name">
              </div>
            </div>
            <div class="userdetailheadcont userdetailseperator">
              Files
            </div>
            <div class="files">
              <div>KTP</div>
              <div>IJAZAH</div>
              <div>NPWP</div>
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