<template>
    <div class="pagehome">
        <HeaderComp/>
        <div>
          page {{user}}
            <v-btn
                @click="logout"
            >
            Log Out
            </v-btn>
        </div>
    </div>
</template>
<script>
import HeaderComp from '~/components/headerComp.vue';
export default {
    components: { HeaderComp },
    data() {
        return {
            bgColor: "#0957DE"
        };
    },
    computed: {
        user() {
            const data = JSON.parse(localStorage.getItem("userinfo")).idAdmin;
            return data;
        }
    },
    methods: {
        logout() {
            localStorage.clear();
            this.$router.push({ name: "index" });
        }
    },

}
</script>

<style>
/* .v-main__wrap{
  background-color: #9BC9FB
} */
.pagehome{
    display: flex;
    align-items: center;
    justify-content: center;
    height: 100vh;
    background-color: #9BC9FB;
}
</style>