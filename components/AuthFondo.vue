<template>
  <div>
    <!-- <v-layout>
        <v-flex sm12 md6 offset-md3>
          <v-card elevation="4" light tag="section">
            <v-card-title>
              <v-layout align-center justify-space-between >
                <h3 class="headline">
                  {{ platformName }}
                </h3>
                <v-flex>
                   </v-flex>
              </v-layout>
            </v-card-title>
            
            <v-card-text>
              <p>Correo y Contraseña</p>
              <v-form>
                <v-text-field
                              outline
                              label="Username"
                              type="text"
                                                            ></v-text-field>
                <v-text-field
                              outline
                              hide-details
                              label="Password"
                              type="password"
                              ></v-text-field>
              </v-form>
            </v-card-text>
            <v-divider></v-divider>
        
              <v-btn color="info" flat>
                
              </v-btn>
              <v-spacer></v-spacer>
              
                
               
              
            </v-card-actions>
          </v-card>
        </v-flex>
        <v-flex sm12 md6 offset-md3>
          
        </v-flex>
      </v-layout> -->
    <v-sheet color="transparent" tile>
      <v-row justify="center" align="center">
        <v-col cols="12" sm="4">
          <div>
            <v-sheet
              width="500"
              height="300"
              color="transparent"
              elevation="10"
              rounded="xl"
              class="px-16 ma-4"
            >
              <v-text-field
                v-model="usuario"
                height="40"
                label="E-mail"
                :rules="rules"
                hide-details="auto"
                value="usuario"
              >
              </v-text-field>

              <v-spacer></v-spacer>
              <v-text-field v-model="pass" label="Contraseña"> </v-text-field>
              <v-spacer></v-spacer>
              <v-btn
                to="/miusuario"
                x-large
                icon
                color="white"
                @click.stop="login"
              >
                <v-icon x-large>mdi-account-circle-outline</v-icon>
                <!-- to="../pages/miusuario" -->
              </v-btn>
              <v-btn color="white">
                <v-icon x-large>mdi-cancel</v-icon>
              </v-btn>
            </v-sheet>
          </div>
        </v-col>
      </v-row>
    </v-sheet>
  </div>
</template>

<script>
import {
  getAuth,
  signInWithEmailAndPassword /* , createUserWithEmailAndPassword */,
} from "firebase/auth";

export default {
  data() {
    return {
      darkTheme: true,
      platformName: "Iniciar sesión",
      password: false,
      username: false,
      rules: [
        (value) => !!value || "Required.",
        (value) => (value && value.length >= 3) || "Min 3 characters",
      ],
      usuario: "",
      pass: "",
    };
  },
  methods: {
    login() {
      // eslint-disable-next-line no-console
      console.log(this.usuario + " frtyu" + this.pass + " u" + this.username);

      const auth = getAuth(); /*
signInWithEmailAndPassword(auth,this.email,this.usuario); */
      signInWithEmailAndPassword(auth, this.usuario, this.pass)
        .then((res) => {
          // eslint-disable-next-line no-console
          console.log(res + "derty");
          // eslint-disable-next-line no-console
          console.table(res);
          this.$router.push("/miusuario");
        })
        .catch((error) => {
          // eslint-disable-next-line no-console
          console.log(error + "nono");
        });
    },
  },
};
</script>

<style>
.v-btn,
.v-card {
  border-radius: 4px;
}
.v-card__title {
  text-transform: uppercase;
}
</style>
