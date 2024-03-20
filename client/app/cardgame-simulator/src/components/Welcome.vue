<template>
    <v-container class="h-100 w-100">
      <v-row class="
        d-flex
        flex-xl-nowrap
        flex-lg-nowrap
        flex-md-wrap
        flex-sm-wrap
        align-center
        justify-space-around
        fill-height"
      >
        <v-col cols="auto" class="
          d-flex
          flex-column
          align-left
          justify-center"
        >
          <div class="text-h5">Welcome to</div>
          <div class="text-h2 font-weight-bold">Cardgame Simulator</div>
        </v-col>
        <v-col cols="auto">
          <v-sheet
            width="28rem"
            height="25.8rem"
            id="login-form"
            class="pa-10 rounded-xl bg-grey-lighten-4"
          >
            <v-text-field
              prepend-icon="mdi-email"
              label="Email"
              type="email"
              variant="outlined"
              hide-details="auto"
              bg-color="white"
              class="rounded"
            ></v-text-field>
            <v-text-field
              prepend-icon="mdi-lock"
              label="Password"
              type="password"
              variant="outlined"
              hide-details="auto"
              bg-color="white"
              class="mt-5 rounded"
            ></v-text-field>
            <v-card-actions class="mt-5 mb-8">
              <v-btn
                color="primary"
                variant="flat"
                size="x-large"
                width="24.8rem"
                height="3.6rem"
              >login</v-btn>
            </v-card-actions>
            <v-divider></v-divider>
            <v-card-actions class="mt-8">
              <v-btn
                color="orange-darken-1"
                variant="flat"
                size="x-large"
                width="24.8rem"
                height="3.6rem"
                @click="dialog = true"
              >create new account</v-btn>
            </v-card-actions>
            <v-dialog v-model="dialog" width="auto">
              <v-sheet width="30rem" height="32rem" class="pa-5">
                <v-row>
                  <v-col class="
                    my-5
                    ml-5
                    text-h3
                    font-weight-bold"
                  >Sign Up</v-col>
                  <v-col class="pa-0 d-flex flex-row justify-end">
                    <v-btn
                      variant="plain"
                      density="compact"
                      icon="mdi-close"
                      size="x-large"
                      @click="dialog = false"
                    ></v-btn>
                  </v-col>
                </v-row>
                <v-divider></v-divider>
                <v-form fast-fail @submit.prevent class="pa-5">
                  <v-text-field
                    prepend-icon="mdi-account-circle"
                    v-model="username"
                    :rules="usernameRules"
                    label="User name"
                    variant="outlined"
                    hide-details="auto"
                    class="rounded"
                  ></v-text-field>
                  <v-text-field
                    prepend-icon="mdi-email"
                    v-model="email"
                    :rules="emailRules"
                    label="Email"
                    type="email"
                    variant="outlined"
                    hide-details="auto"
                    class="mt-5 rounded"
                  ></v-text-field>
                  <v-text-field counter="32"
                    prepend-icon="mdi-lock"
                    v-model="password"
                    :rules="passwordRules"
                    label="Password"
                    type="password"
                    variant="outlined"
                    hide-details="auto"
                    class="mt-5 rounded"
                  ></v-text-field>
                  <v-btn
                    color="orange-darken-1"
                    variant="flat"
                    size="x-large"
                    class="mt-10"
                    block
                  >sign up</v-btn>
                </v-form>
              </v-sheet>
            </v-dialog>
          </v-sheet>
        </v-col>
      </v-row>
    </v-container>
  </template>
  
  <script setup lang="ts">
    import { ref } from 'vue'
  
    const dialog = ref<boolean>(false)
  
    const username = ref<string>('')
    const usernameRules = [
      (value:string) => requireRule(value),
      (value:string) => usernameRule(value),
      (value:string) => minCharRule(value)
    ]
  
    const email = ref<string>('')
    const emailRules = [
      (value:string) => requireRule(value),
      (value:string) => emailRule(value)
    ]
  
    const password = ref<string>('')
    const passwordRules = [
      (value:string) => requireRule(value),
      (value:string) => passwordRule(value)
    ]
  
    const requireRule = (value:string) => {
      return value ? true : 'この項目は必須です'
    }
  
    const usernameRule = (value:string) => {
      return value?.length >= 3 ? true : '3文字未満のユーザ名です'
    }
  
    const minCharRule = (value:string) => {
      return value?.length >= 3 ? true : '3文字未満のユーザ名です'
    }
  
    const emailRule = (value:string) => {
      return /^[a-zA-Z0-9_.+-]+@([a-zA-Z0-9][a-zA-Z0-9-]*[a-zA-Z0-9]*\.)+[a-zA-Z]{2,}$/i.test(value) ? true : '無効なメールアドレスです'
    }
  
    const passwordRule = (value:string) => {
      return /^(?=.*[A-Z])(?=.*[!-/:-@[-`{-~])[a-zA-Z0-9!-/:-@[-`{-~]{8,32}$/i.test(value) ? true : '半角英数字及び記号を含む8文字以上32文字以下'
    }
  </script>
