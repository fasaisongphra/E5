<template>
    <div>
      <v-img
        class="mx-auto my-6"
        max-width="150"
        src="https://static.vecteezy.com/system/resources/previews/014/919/663/original/dashboard-3d-render-icon-png.png"
      ></v-img>
  
      <v-card
        class="mx-auto pa-12 pb-8"
        elevation="8"
        max-width="448"
        rounded="lg"
      >
        <!-- Sign Up Title -->
        <div class="text-subtitle-1 text-medium-emphasis">สมัครสมาชิก</div>
  
        <!-- Name Input Field -->
        <v-text-field
          v-model="name"
          density="compact"
          placeholder="ชื่อของคุณ"
          prepend-inner-icon="mdi-account-outline"
          variant="outlined"
          aria-label="Name"
        ></v-text-field>
  
        <!-- Email Input Field -->
        <v-text-field
          v-model="email"
          density="compact"
          placeholder="Email address"
          prepend-inner-icon="mdi-email-outline"
          variant="outlined"
          aria-label="Email address"
        ></v-text-field>
  
        <!-- Password Input Field -->
        <v-text-field
          v-model="password"
          :append-inner-icon="visible ? 'mdi-eye-off' : 'mdi-eye'"
          :type="visible ? 'text' : 'password'"
          density="compact"
          placeholder="สร้างรหัสผ่าน"
          prepend-inner-icon="mdi-lock-outline"
          variant="outlined"
          @click:append-inner="visible = !visible"
        ></v-text-field>
  
        <v-btn @click="doSignUp" class="custom-signup-btn mb-8" size="large" block>
          <v-icon left>mdi-account-plus</v-icon>
          ลงทะเบียน
        </v-btn>
  
        <v-card-text class="text-center">
          <a
            class="text-blue text-decoration-none"
            href="#"
            @click.prevent="goToLogin"
          >
            กลับไปที่หน้าล็อกอิน <v-icon icon="mdi-chevron-right"></v-icon>
          </a>
        </v-card-text>
      </v-card>
    </div>
  </template>
  
  <script>
  import axios from 'axios';
  export default {
    data: () => ({
      visible: false,
      name: "",
      email: "",
      password: ""
    }),
    methods: {
      async doSignUp() {
        let formData = {
          name: this.name,
          email: this.email,
          password: this.password
        };
        try {
          const res = await axios.post('http://localhost:7000/signup', formData);
          const data = await res.data;
          if (data.status === 'success') {
            this.$router.replace('/login');
          } else {
            console.error('Error signing up:', data.message);
          }
        } catch (error) {
          console.error('Sign up failed:', error);
        }
      },
      goToLogin() {
        this.$router.push('/login');
      }
    }
  };
  </script>
  
  <style scoped>
  .custom-signup-btn {
    background-color: #4caf50; /* สีเขียว */
    color: white;
    font-weight: bold;
    font-size: 18px;
    padding: 12px 24px;
    border-radius: 8px;
    box-shadow: 0px 4px 6px rgba(0, 0, 0, 0.1);
    transition: background-color 0.3s ease, transform 0.3s ease;
  }
  
  .custom-signup-btn:hover {
    background-color: #388e3c; /* สีเขียวเข้มขึ้นเมื่อ hover */
    transform: translateY(-2px); /* เอฟเฟกต์ยกขึ้นเมื่อ hover */
  }
  </style>
  