
<template>
<v-card>
  <v-card-title>
    <span class="headline">Sign Up</span>
  </v-card-title>
  <v-layout row justify-center>
    <v-form v-model="valid" ref="form" lazy-validation>
      <v-flex xs12 sm6 md12>
        <v-text-field
          label="Name"
          v-model="name"
          :rules="nameRules"
          :counter="10"
          required
        ></v-text-field>
        <v-text-field
          label="E-mail"
          v-model="email"
          :rules="emailRules"
          required
        ></v-text-field>
        <v-select
          label="Item"
          v-model="select"
          :items="items"
          :rules="[v => !!v || 'Item is required']"
          required
        ></v-select>
        <v-checkbox
          label="Do you agree?"
          v-model="checkbox"
          :rules="[v => !!v || 'You must agree to continue!']"
          required
        ></v-checkbox>
      </v-flex>
        <v-btn
          @click="submit"
          :disabled="!valid"
        >
          submit
        </v-btn>
        <v-btn @click="clear">clear</v-btn>
      </v-form>
    </v-layout>
  </v-card>
  
</template>
 

 <script>
  import axios from 'axios'

  export default {
    data: () => ({
      valid: true,
      name: '',
      nameRules: [
        v => !!v || 'Name is required',
        v => (v && v.length >= 6) || 'Name must be less than 10 characters'
      ],
      email: '',
      emailRules: [
        v => !!v || 'E-mail is required',
        v => /^\w+([.-]?\w+)*@\w+([.-]?\w+)*(\.\w{2,3})+$/.test(v) || 'E-mail must be valid'
      ],
      select: null,
      items: [
        'Item 1',
        'Item 2',
        'Item 3',
        'Item 4'
      ],
      checkbox: false
    }),

    layout: 'main',

    methods: {
      submit () {
        if (this.$refs.form.validate()) {
          // Native form submission is not yet supported
          axios.post('/api/submit', {
            name: this.name,
            email: this.email,
            select: this.select,
            checkbox: this.checkbox
          })
        }
      },
      clear () {
        this.$refs.form.reset()
      }
    }
  }
</script>


  // <v-layout row justify-center>
  //   <v-dialog v-model="dialog" persistent max-width="500px">
  //     <v-card>
  //       <v-card-title>
  //         <span class="headline">Sign Up</span>
  //       </v-card-title>
  //       <v-card-text>
          // <v-container grid-list-md>
          //   <v-layout wrap>
          //     <v-flex xs12 sm6 md6>
          //       <v-text-field label="First name" required></v-text-field>
          //     </v-flex>             
  //             <v-flex xs12 sm6 md6>
  //               <v-text-field
  //                 label="Last name"                                   
  //                 required
  //               ></v-text-field>
  //             </v-flex>
  //             <v-flex xs12>
  //               <v-text-field label="Email" required></v-text-field>
  //             </v-flex>
  //             <v-flex xs12>
  //               <v-text-field label="Password" type="password" required></v-text-field>
  //             </v-flex>  
  //             <v-flex xs12>
  //               <v-text-field label="Company" type="company" required></v-text-field>
  //             </v-flex>              
  //           </v-layout>
  //         </v-container>
  //         <small>*indicates required field</small>
  //       </v-card-text>
  //       <v-card-actions>
  //         <v-spacer></v-spacer>         
  //         <v-btn color="blue" flat @click.native="dialog = false"><h3>Submit</h3></v-btn>
  //       </v-card-actions>
  //     </v-card>
  //   </v-dialog>
  // </v-layout>