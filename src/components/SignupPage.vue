
<template>
  <v-container class="my-5">
    <div class="signup container mt-5">
      <v-card
        color="white"
        class="mx-auto pa-9 rounded-lg card card-container"
        elevation="2"
        height="100%"
        width="770"
      >
        <div class="header">
          <v-row>
            <div class="header-inner">
              <h3 class="form-title">Sign Up</h3>
            </div>
          </v-row>
        </div>

        <div class="form-div">
          <v-form class="pa-1 mt-5">
            <v-row>
              <v-col cols="12" md="6">
                <div>Company name*</div>
                <v-text-field
                  persistent-hint
                  outlined
                  dense
                  :rules="rules.companyName"
                ></v-text-field>
              </v-col>

              <v-col>
                <div>Company logo*</div>
                <!-- <v-text-field
                  class="mt-2"
                  persistent-hint
                  outlined
                  dense
                ></v-text-field> -->

                <v-file-input
                  v-model="files"
                  dense
                  multiple
                  prepend-icon=""
                  append-icon="mdi-paperclip"
                  outlined
                  :rules="rules.logo"
                >
                </v-file-input>
              </v-col>
            </v-row>

            <v-row class="my-0">
              <v-col cols="12" md="6">
                <div>Company domain*</div>
                <v-text-field
                  color="#e05729 "
                  persistent-hint
                  outlined
                  dense
                ></v-text-field>
              </v-col>

              <v-col cols="12" md="6">
                <div>Company email*</div>
                <v-text-field
                  color="#e05729 "
                  persistent-hint
                  outlined
                  dense
                  :rules="rules.email"
                ></v-text-field>
              </v-col>
            </v-row>

            <v-row class="my-0">
              <v-col cols="12" md="6" lg="6">
                <div>Password*</div>
                <v-text-field
                  :append-icon="show1 ? 'mdi-eye' : 'mdi-eye-off'"
                  :type="showPassword ? 'text' : 'password'"
                  color="#e05729 "
                  hint="8 characters, alpha & numeric & 1 special character"
                  @click:append="showPassword = !showPassword"
                  outlined
                  dense
                ></v-text-field>
              </v-col>

              <v-col>
                <div>Confirm password*</div>
                <v-text-field
                  :append-icon="show1 ? 'mdi-eye' : 'mdi-eye-off'"
                  :type="showPassword ? 'text' : 'password'"
                  color="#e05729 "
                  hint="8 characters min, alpha & numeric & 1 special character"
                  @click:append="showPassword = !showPassword"
                  outlined
                  dense
                ></v-text-field>
              </v-col>
            </v-row>
            <div class="policy-div">
              <v-card-text>
                <p class="policy-text">
                  By signing up you agree to the
                  <span>terms and conditions</span> and
                  <span>privacy policy</span> of this platform
                </p>
              </v-card-text>
            </div>
            <div class="text-center mb-3 btn-submit">
              <v-card-actions>
                <v-btn
                  block
                  depressed
                  class="orange"
                  :style="{
                    backgroundColor: changeBackgroundColor
                      ? '#e05729 !important'
                      : '',
                    color: changeBackgroundColor ? 'white !important' : 'black',
                    textTransform: 'capitalize',
                  }"
                  >Sign Up</v-btn
                >
              </v-card-actions>
            </div>
            <div class="sign-text">
              <v-card-text>
                <p class="policy-text">
                  Already registered?
                  <span>Sign in </span> instead
                </p>
              </v-card-text>
            </div>
          </v-form>
        </div>
      </v-card>
    </div>
  </v-container>
</template>


<script>
export default {
  data() {
    return {
      changeBackgroundColor: true,
      files: [],
      showPassword: false,
      rules: {
        companyName: [
          (v) => (v || "").length > 0 || "Company name is required",
        ],
        logo: [
          (v) => !!v || "File is required",
          (v) => (v && v.length > 0) || "File is required",
        ],
        email: [
          (v) => !!v || "Email is required",
          (v) => {
            const pattern =
              /^(([^<>()[\]\\.,;:\s@"]+(\.[^<>()[\]\\.,;:\s@"]+)*)|(".+"))@((\[[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}])|(([a-zA-Z\-0-9]+\.)+[a-zA-Z]{2,}))$/;
            return pattern.test(v) || "Invalid e-mail";
          },
        ],
      },
    };
  },

  watch: {
    files: function () {
      console.log(this.files);
    },
  },
};
</script>

<style scoped>
.signup.container {
}

.header {
  position: relative;
  top: 40px;
}

.header-inner {
  margin: 0 auto;
}

.form-div {
  position: relative;
  top: 4.125rem;
}

.form-title {
  color: rgb(78, 75, 75);
}

.my-input.v-input.v-input__slot {
  border-radius: 100px;
}

.border-outline:focus {
  outline: #e05729;
}

/* .v-text-field--outlined >>> fieldset:focus {
  outline: rgba(192, 0, 250, 0.986);
} */

.policy-div {
  margin: 0 auto;
}

.policy-text span {
  color: #e05729;
}

.policy-text {
  width: 95%;
  text-align: center;
}

.btn-submit {
  width: 30%;
  position: relative;
  bottom: 20px;
  margin: 0 auto;
}

.sign-text {
  position: relative;
  bottom: 30px;
}

/* Media queries */
@media screen and (max-width: 380px) {
  /* .v-chip {
    max-width: 500px;
  } */
}

@media screen and (max-width: 600px) {
  .card.card-container {
    background: red;
  }
}
</style>