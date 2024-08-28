<template>
    <v-container>
      <v-row>
        <v-col cols="12" md="8" offset-md="2">
          <v-card>
            <v-card-title>
              <span class="headline">Contact Us</span>
            </v-card-title>
            
            <v-card-text>
                ติดต่อฉันได้ที่นี้
              </v-card-text>

            <v-card-subtitle>
            หากท่านมีข้อสงสัยกรุณากรอกแบบฟอร์มด้านล่างนี้ แล้วเราจะติดต่อคุณกลับไป
            </v-card-subtitle>
  
            <v-card-text>
              <v-form @submit.prevent="submitForm">
                <v-text-field
                  v-model="name"
                  label="Name"
                  required
                  :rules="[rules.required]"
                ></v-text-field>
  
                <v-text-field
                  v-model="email"
                  label="Email"
                  required
                  :rules="[rules.required, rules.email]"
                ></v-text-field>
  
                <v-textarea
                  v-model="message"
                  label="Message"
                  rows="4"
                  required
                  :rules="[rules.required]"
                ></v-textarea>
  
                <v-btn type="submit" color="primary">Send</v-btn>
              </v-form>
            </v-card-text>
          </v-card>
        </v-col>
      </v-row>
    </v-container>
  </template>
  
  <script>
  export default {
    data() {
      return {
        name: '',
        email: '',
        message: '',
        rules: {
          required: value => !!value || 'Required.',
          email: value => /.+@.+\..+/.test(value) || 'E-mail must be valid.',
        },
      };
    },
    methods: {
      submitForm() {
        // Handle form submission
        // For example, send data to an API or display a success message
        console.log('Name:', this.name);
        console.log('Email:', this.email);
        console.log('Message:', this.message);
        this.$refs.form.reset(); // Reset the form fields after submission
      },
    },
  };
  </script>
  
  <style scoped>
  .headline {
    font-weight: bold;
  }
  </style>
  