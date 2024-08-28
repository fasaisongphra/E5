<template>
    <div>
      <v-container class="mt-12">
        <v-row>
          <v-col>
            <v-card>
              <v-card-title class="text-h5">ยินดีต้อนรับสู่หน้า Home</v-card-title>
              <v-card-text>
                <!-- นี่คือหน้าแรกของแอปพลิเคชันของคุณ -->
              </v-card-text>

              <v-img
                  src="https://th.bing.com/th/id/OIP.EtCREPKYyuUhwRJcy1Q6jwHaEK?rs=1&pid=ImgDetMain/300x300"
                  alt="About Us Image"
                  contain
                ></v-img>


              <v-card-actions>
                <!-- <v-btn color="primary" @click="$router.push('/datatable')">ดูรายชื่อสมาชิก</v-btn> -->
              </v-card-actions>
            </v-card>
          </v-col>
        </v-row>
      </v-container>
    </div>
  </template>
  
  <script>
  export default {
    name: 'Home',
  }
  </script>
  