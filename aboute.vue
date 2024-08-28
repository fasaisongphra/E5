<template>
  <v-container>
    <v-row>
      <v-col cols="12" md="8" offset-md="2">
        <v-card>
          <v-card-title>
            <span class="headline">About Us</span>
          </v-card-title>

          <v-card-subtitle>
            <!-- Learn more about our company and team. -->
          </v-card-subtitle>

          <v-card-text>
            <v-row>
              <v-col cols="12" md="6">
                <v-img
                  src="\api_e5_2567\fasai.png"
                  alt="About Us Image"
                  contain
                ></v-img>
              </v-col>
              <v-col cols="12" md="6">
                <v-card>
                  <v-card-title>
                    ฟ้าใส  ทรงพระ
                  </v-card-title>
                  <v-card-text>
                    โทรศัพท์ : 0928304464 <br>
                    ที่อยู่ : 152/1 หมู่2 บ้านหนองรวก ตำบลนาหนองทุ่ม <br> อำเภอแก้งคร้อ จังหวัดชัยภูมิ 36150 
                  </v-card-text>
                </v-card>

                <v-card class="mt-4">
                  <v-card-title>
                    เสนอแนะ
                  </v-card-title>
                  <v-card-text>
                    IT Support คืออะไร? <br>  คุณสมบัติและทักษะที่ต้องมี
              category_1_1 6 <br>
              เรียนจบไอที สามารถทำงานในสายงานใดได้บ้าง?
                  </v-card-text>
                </v-card>
              </v-col>
            </v-row>
          </v-card-text>
        </v-card>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
export default {
  name: 'About',
};
</script>

<style scoped>
.headline {
  font-weight: bold;
}
</style>
