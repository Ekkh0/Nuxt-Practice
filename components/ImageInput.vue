<template>
    <div class="parent">
        <div class="containercardouter">
            <div class="containercard">
                <input id="fileInput1" type="file" accept="image/*" @input="updateValue1">
                <input id="inputbtn" type="button" @click="upload1" />
                <img v-if="image1" :src="image1" class="imagepreview"/>
                <div class="cardinsidecontainer">
                    <div class="cardinside">
                        <div class="cardimgcont">
                            <img :src="require('@/assets/terminal.svg')" alt="" class="terminallogo">
                        </div>
                        <p>KTP</p>
                    </div>
                </div>
            </div>
            <div class="containercard">
                <input id="fileInput2" type="file" accept="image/*" @input="updateValue2">
                <input id="inputbtn" type="button" @click="upload2" />
                <img v-if="image2" :src="image2" class="imagepreview"/>
                <div class="cardinsidecontainer">
                    <div class="cardinside">
                        <div class="cardimgcont">
                            <img :src="require('@/assets/Ijazah.svg')" alt="" class="terminallogo">
                        </div>
                        <p>Ijazah</p>
                    </div>
                </div>
            </div>
            <div class="containercard">
                <input id="fileInput3" type="file" accept="image/*" @input="updateValue3">
                <input id="inputbtn" type="button" @click="upload3" />
                <img v-if="image3" :src="image3" class="imagepreview"/>
                <div class="cardinsidecontainer">
                    <div class="cardinside">
                        <div class="cardimgcont">
                            <img :src="require('@/assets/npwp.svg')" alt="" class="terminallogo">
                        </div>
                        <p>NPWP</p>
                    </div>
                </div>
            </div>
            <div class="containercard">
                <input id="fileInput4" type="file" accept="image/*" @input="updateValue4">
                <input id="inputbtn" type="button" @click="upload4" />
                <img v-if="image4" :src="image4" class="imagepreview"/>
                <div class="cardinsidecontainer">
                    <div class="cardinside">
                        <div class="cardimgcont">
                            <img :src="require('@/assets/Photo.svg')" alt="" class="terminallogo">
                        </div>
                        <p>Photo</p>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
    export default{
        data(){
            return{
                input1: undefined,
                imageFile1: undefined,
                image1: undefined,
                input2: undefined,
                imageFile2: undefined,
                image2: undefined,
                input3: undefined,
                imageFile3: undefined,
                image3: undefined,
                input4: undefined,
                imageFile4: undefined,
                image4: undefined,
            }
        },
        mounted(){
            this.input1 = document.getElementById('fileInput1')
            this.input2 = document.getElementById('fileInput2')
            this.input3 = document.getElementById('fileInput3')
            this.input4 = document.getElementById('fileInput4')
        },
        methods:{
            upload1(){
                document.getElementById('fileInput1').click()
            },
            upload2(){
                document.getElementById('fileInput2').click()
            },
            upload3(){
                document.getElementById('fileInput3').click()
            },
            upload4(){
                document.getElementById('fileInput4').click()
            },
            updateValue1(event){
                this.imageFile1 = event.target.files[0]
                this.image1 = this.imageFile1 ? URL.createObjectURL(this.imageFile1) : undefined
                this.$emit('input1', this.imageFile1)
            },
            updateValue2(event){
                this.imageFile2 = event.target.files[0]
                this.image2 = this.imageFile2 ? URL.createObjectURL(this.imageFile2) : undefined
                this.$emit('input2', this.imageFile2)
            },
            updateValue3(event){
                this.imageFile3 = event.target.files[0]
                this.image3 = this.imageFile3 ? URL.createObjectURL(this.imageFile3) : undefined
                this.$emit('input3', this.imageFile3)
            },
            updateValue4(event){
                this.imageFile4 = event.target.files[0]
                this.image4 = this.imageFile4 ? URL.createObjectURL(this.imageFile4) : undefined
                this.$emit('input4', this.imageFile4)
            },
        }
    }
</script>

<style>
    @import url('https://fonts.googleapis.com/css2?family=Lato:wght@400;700;900&display=swap');

    .containercardouter{
        display: grid;
        grid-template-columns: repeat(2, 200px);
        grid-gap: 30px;
        padding: 10px;
        padding-bottom: 30px;
    }

    .containercard{
        width: 200px;
        height: 90px;
        position: relative;
        border-radius: 10px;
        box-shadow: 1px 1px 5px rgba(128, 128, 128, 0.35);
        outline: solid 0px #0000FF;
        transition: all 0.1s ease-in-out;
        overflow: hidden;
    }

    .containercard:hover{
        /* background-color: black; */
        outline: solid 3px #0000FF;
    }

    #fileInput1, #fileInput2, #fileInput3, #fileInput4{
        display: none;
    }

    #inputbtn{
        cursor: pointer;
        position: absolute;
        z-index: 2;
        left: 0;
        top: 0;
        background-color: transparent;
        border: none;
        width: 100%;
        height: 100%;
    }

    .imagepreview{
        position: absolute;
        z-index: 1;
        left: 0;
        top: 0;
        width: 100%;
        height: 100%;
        object-fit: cover;
        opacity: 0.15;
    }

    .icon{
        position: absolute;
        width: 20px;
        height: 20px;
        left: 0;
        height: 0;
    }

    .cardinsidecontainer{
        height: 100%;
        width: 100%;
        display: flex;
        align-items: center;
    }

    .cardinside{
        z-index: 3;
        display: flex;
        margin-left: 15px;
        height: 50%;
        align-items: center;
    }

    .cardinside > p{
        font-family: lato;
        font-weight: 700;
        font-size: 15px;
        margin: 0;
        padding-left: 5px;
    }

    .terminallogo{
        filter: invert(20%) sepia(71%) saturate(6150%) hue-rotate(246deg) brightness(107%) contrast(109%);
        height: 100%;
    }

    .cardimgcont{
        height: 100%;
        padding: 5px;
        border-radius: 100px;
        background-color: #E4E1FF;
    }

</style>