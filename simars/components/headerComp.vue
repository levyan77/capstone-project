<template>
    <div class="microHeader">
        <div class="headerContent">
            <a class="Logo" :style="{backgroundImage: `url(${images.company})`}" href="/"></a>
            <div class="NavItems">
                <a class="Logo2" :style="{backgroundImage: `url(${images.ava})`}" href="/" ></a>
                <div class="NavLink">{{user}}</div>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: "HeaderComponent",
    data:() => ({
          images: {
                company: require('~/assets/LogoCompany.png'),
                ava: require('~/assets/Ava.png')
            }
    }),
    computed: {
     user() {
        const data = JSON.parse(localStorage.getItem("userinfo")).idAdmin;
        return data;
     }
    },
}
</script>
<style>
.v-application a{
    text-decoration: none;
    color: rgba(255, 255, 255,0.7) !important ;
}
.v-application a:hover{
    color: rgba(255, 255, 255,1) !important ;
}
.microHeader{
    top: 0;
    position: absolute;
    z-index: 9999;
    background-color: #0957DE;
    width: 100%;
    height: 70px;
}
.headerContent{
    width: 100%;
    height: 100%;
    display: flex;
    flex-direction: row;
    align-items: center;
}
.Logo{
    width: 200px;
    min-width: 200px;
    height: 50px;
    min-height: 50px;
    background-size: contain;
    background-repeat: no-repeat;
    background-position: center center;
    opacity: .8;
    margin-right: 40px;
}.Logo2{
    width: 60px;
    min-width: 0;
    height: 50px;
    min-height: 50px;
    background-size: contain;
    background-repeat: no-repeat;
    background-position: center center;
    opacity: .8;
    margin-right: 0;
}
.Logo:hover{
    opacity: 1;
}
.Logo2:hover{
    opacity: 1;
}
.NavItems{
    flex-grow: 1;
    height: 100%;
    display: flex;
    flex-direction: row;
    align-items: center;
    position: relative;
    justify-content: right;
}
.NavLink{
    font-size: 18px;
    font-family: 'Cinzel', serif;
    font-weight: 600;
    letter-spacing: 3px;
    opacity: .8;
    color: #fff;
    display: flex;
    flex-direction: row;
    align-items: center;
    padding: 3px 0px;
    margin: 0px 20px;
    text-transform: uppercase;
    border-top: 3px solid transparent;
    border-bottom: 3px solid transparent;
}
</style>