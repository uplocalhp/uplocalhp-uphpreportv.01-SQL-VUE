<template>

  <v-app>
    <v-container>
    <v-form @submit.prevent="handleSubmit" v-model="valid"
    >
      <v-card
          class="mx-auto my-12"
          max-width="374"
      >
        <v-img
            height="350"
            src="https://upload.wikimedia.org/wikipedia/th/thumb/a/a4/UPHosLogo.svg/1024px-UPHosLogo.svg.png"
        ></v-img>
        <v-card-title>ระบบแจ้งซ่อม</v-card-title>
          <div>
              <v-card-text>
                <v-text-field 
                  v-model="username"
                  label="Username"
                  hide-details="auto"
                  :rules="emailRules"
                  required
                ></v-text-field>
                <v-text-field 
                  v-model="password"
                  label="Password" 
                  type="password" 
                  hide-details="auto"
                  :rules="nameRules"
                  required
                ></v-text-field>
              </v-card-text>
              <v-card-actions >
              <v-btn color="success" type="submit" value="submit" :disabled="!valid">login</v-btn>
              </v-card-actions>
          </div>
      </v-card> 
    </v-form>
    
    
  </v-container>
  </v-app>
</template>

<script>
  export default {
    name: 'HelloWorld',

    data: () => ({
      valid: true,
      username :'',
      password :'',
      nameRules: [
        v => !!v || 'Password is required',
        v => (v && v.length >= 6) || 'Password must be less than 6 characters',
      ],
       emailRules: [
        v => !!v || 'Username is required',
      ],
    }),
    methods: {
      handleSubmit (e) {
        e.preventDefault();
        const { username, password } = this;
        console.log(username,password);
          this.login({username,password})
      },
    },
  }
</script>
