<template>
<div class="page">
    <v-row justify="center" align="center">
    <v-img
      max-height="fit-content"
      max-width="fit-content"
      contain
      :src="images.sample"
    ></v-img>
    <v-col cols="12" sm="8" md="6">
      <v-card-title
      style="
             color: white;
             text-align: center;
             display: block;
             padding-bottom: 100px;
             font-size: 30px;
             font-weight: bold;
             font-family: Poppins, sans-serif;">
        Hospital Management System
      </v-card-title>
      <v-card
      class="rounded-lg"
      height="445px"
      width="445px"
      style="margin:auto">
        <v-card-title
        style="
        color: #0957DE;
        font-weight: 800;
        font-size: 50px;
        display: block;
        text-align: center;
        font-family: Poppins, sans-serif;
        margin-bottom: 50px;
        padding-top: 40px
        ">
          LOGIN
        </v-card-title>
        <div class="idAdmin">
          <label class="inputTitle">ID Admin</label>
          <v-text-field
              v-model="idadmin"
              style="margin-top: 10px;"
              label="Id Admin"
              placeholder="ID Admin"
              outlined
              dense
              type="text"
          ></v-text-field>
        </div>
        <div class="password">
          <label class="inputTitle">Password</label>
          <v-text-field
              v-model="password"
              style="margin-top: 10px;"
              label="Password"
              placeholder="Password"
              outlined
              dense
              type="password"
          ></v-text-field>
        </div>
        <v-card-actions
        class="justify-center"
        style="
          margin-left: 20px;
          margin-right: 20px;
        ">
         <v-btn
          block
          color="#0957DE"
          elevation="2"
          dark
          height="60px"
          @click="login"
         >Masuk</v-btn>
         </v-card-actions>
      </v-card>
    </v-col>
    <v-img
      max-height="fit-content"
      max-width="fit-content"
      contain
      :src="images.sample2"
    ></v-img>
  </v-row>

</div>
</template>

<script>
import axios from 'axios'
export default {
  name: 'IndexPage',
  data:() => ({
          textColor: 'red',
          idadmin:'',
          password:'',
          images: {
                sample: require('~/assets/Character.png'),
                sample2: require('~/assets/character-2.png')
            }
    }),
  methods:{
    async login()
    {
      const result = await axios.get(
        `http://localhost:3000/user?idAdmin=${this.idadmin}&password=${this.password}`
      )

      if(result.status === 200 && result.data.length>0 )
      {
        localStorage.setItem("userinfo",JSON.stringify(result.data[0]))
        this.$router.push({name: 'adminHome'})
      }
      console.warn(result)
    }
  }
}
</script>

<style>
/* .v-main__wrap{
  background-color: #0957DE
} */
.page{
    display: flex;
    align-items: center;
    justify-content: center;
    height: 100vh;
    background-color: #0957DE;
}
.idAdmin{
  margin-left: 30px;
  margin-right: 30px;
}
.password{
  margin-left: 30px;
  margin-right: 30px;
}
.inputTitle{
    font-size: large;
    font-weight: bold;
}
</style>