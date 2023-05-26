<template>
    <div class="text-xs">
      <div class="background">
        <img :src="require('@/assets/1.jpg')" alt="">
    </div>
    <div class="containerluar">
        <div class="formcontainerregister">
            <h1>Registration</h1>
            <p class="textgrey">Silahkan mengisi formulir berikut dengan sebenar-benarnya. Bantu kami mengenali anda dengan mudah.</p>
            <div class="formpage">
                <div class="progressbarcont">
                    <div class="progressbar" :class="'bar-step-' + step">
                        <div class="progress-step" :class="{'progress-step-active' : step >= 1}"></div>
                        <div class="progress-step" :class="{'progress-step-active' : step >= 2}"></div>
                        <div class="progress-step" :class="{'progress-step-active' : step >= 3}"></div>
                    </div>
                </div>
                <div v-show="step === 1" class="activepage regist1">
                    <p class="headkecil">Contact</p>
                    <p class="textgrey">Masukkan Informasi</p>
                    <div>
                        <div class="inputcont">
                            <label class="label" for="">Name</label>
                            <input class="inputtext registinput" type="text" name="" id="" placeholder="John Carter" v-model="name">
                        </div>
                        <div class="inputcont second">
                            <label class="label" for="">Email</label>
                            <input class="inputtext registinput" type="email" name="" id="" placeholder="Email Address" v-model="email">
                        </div>
                    </div>
                    <div>
                        <div class="inputcont">
                            <label class="label" for="">Phone Number</label>
                            <input class="inputtext registinput" type="tel" name="" id="" placeholder="0888-456-7890" v-model="phone">
                        </div>
                        <div class="inputcont second">
                            <label class="label" for="">University</label>
                            <input class="inputtext registinput" type="text" name="" id="" placeholder="University Name" v-model="uni">
                        </div>
                    </div>
                    <div>
                        <div class="inputcont">
                            <label class="label" for="">Password</label>
                            <input class="inputtext registinput" type="password" name="" id="" placeholder="Password" v-model="pass">
                        </div>
                        <div class="inputcont second">
                            <label class="label" for="">Password Confirmation</label>
                            <input class="inputtext registinput" type="password" name="" id="" placeholder="Password Confirmation" v-model="confpass">
                        </div>
                    </div>
                    <div class="btncont regisbtncont">
                        <router-link tag="button" to="/">Back to Login</router-link >
                        <button id="next" @click="next">Next Step</button>
                    </div>
                </div>
                <div v-show="step === 2" class="activepage regist2">
                    <p class="headkecil">File </p>
                    <p class="textgrey">Upload berkas yang diperlukan</p>
                    <div>
                        <ImageInput @input1="inputimage1($event)" @input2="inputimage2($event)" @input3="inputimage3($event)" @input4="inputimage4($event)" />
                    </div>
                    <div class="btncont regisbtncont">
                        <button id="prev" @click="prev">Previous Step</button>
                        <button id="next" @click="next">Next Step</button>
                    </div>
                </div>
                <div v-show="step === 3" class="activepage finalpage regist3">
                    <img :src="require('@/assets/checkmark.png')" alt="" class="checkimage">
                    <p class="headkecil">Permintaan Akun Berhasil Dikirim</p>
                    <p class="textgrey">Permintaan Anda akan kami verifikasi dalam waktu maksimal 2 x 24 jam. Hasil verifikasi akan kami informasikan melalui email yang didaftarkan.</p>
                    <div class="btncont regisbtncont">
                        <router-link tag="button" to="/">Close</router-link>
                    </div>
                </div>
            </div>
        </div>
      </div>
    </div>
</template>

<script>
export default {
    data(){
        return {
            step: 1,
            name: '',
            email: '',
            phone: '',
            uni: '',
            pass: '',
            confpass: '',
            members: [],
            image1: undefined,
            image1preview: undefined,
            image2: undefined,
            image3: undefined,
            image4: undefined,
        }
    },
    methods:{
        submit:function(){
            if(this.pass == this.confpass){
                console.log('terjalan!')
                this.$axios.post('http://localhost:8000/api/members',{content: this.name}).then(res=>{
                    this.members.unshift(res.data);
                    this.content = '';
                }).catch(error=>{
                    console.log(error);
                }).finally(()=>{

                });
            }
        },
        next:function(){
            this.step++;
        },
        prev:function(){
            this.step--;
        },
        inputimage1(e){
            this.image1=e;
        },
        inputimage2(e){
            this.image2=e;
        },
        inputimage3(e){
            this.image3=e;
        },
        inputimage4(e){
            this.image4=e;
        },
    },
    async fetch(){
        this.members = await fetch('http://localhost:8000/api/members').then(res=>res.json())
    }
}
</script>