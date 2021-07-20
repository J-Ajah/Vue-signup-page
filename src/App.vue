<template>
  <nav>
    <v-app>
      <v-app-bar app color="n" elevation="5">
        <div class="nav-div">
          <v-row>
            <v-col>
              <v-toolbar-title>
                <span>AMALITECH</span>
                <span>-VIRTUAL</span>
              </v-toolbar-title>
            </v-col>
            <!-- <v-spacer></v-spacer> -->

            <v-col class="text-right">
              <v-btn
                color="bgColor"
                class="white--text rounded-lg btn login"
                style="text-transform: capitalize;"
                :style="{
                  backgroundColor: changeBackgroundColor
                    ? '#e05729 !important'
                    : '',
                  color: changeBackgroundColor ? 'white !important' : 'black',
                  textTransform: 'capitalize'
                }"
                small
                depressed
              >
                <span>{{ capitalizeFirstBtnName }}</span>
              </v-btn>
            </v-col>
          </v-row>
        </div>
      </v-app-bar>

      <v-main>
        <router-view />
      </v-main>
    </v-app>
  </nav>
</template>

<script>
export default {
  name: "App",

  data() {
    return {
      btnName: "Login",
      changeBackgroundColor: true,
    };
  },

  computed: {
    capitalizeFirstBtnName() {
      // console.log(
      //   this.btnName.charAt(0).toUpperCase() +
      //     this.btnName.slice(1).toLowerCase()
      // );
      return (
        this.btnName.charAt(0).toLowerCase() +
        this.btnName.slice(1).toLowerCase()
      );
    },
  },
};
</script>

<style scoped>
.bgColor {
  background: #c75532;
}

.nav-div {
  margin: 0 auto;
  width: 90%;
  /* background: rgb(218, 211, 211); */
  /* border: solid 1px black; */
}

/* Media queries */
@media screen and (max-width:380px) {

    .nav-div{
     width: 100%;
         
    }

    .nav-div > .row{
        display: flex;
    }

    
}

</style>