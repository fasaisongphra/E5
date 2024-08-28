<!-- // src/pages/dashboard1.vue -->

<template>
    <v-card-title class="text-h5">ยินดีต้อนรับสู่หน้าแสดงข้อมูลอุณหภูมิ</v-card-title>
              <v-card-text>
                <!-- นี่คือหน้าแรกของแอปพลิเคชันของคุณ -->
              </v-card-text>
  <div>
    <h1 :title="id">{{ msg }}</h1>
    <div><h1>{{ status }}</h1></div>
    <div>
      <v-btn class="ma-2" color="primary">
        {{ status}}
        <v-icon icon="mdi-checkbox-marked-circle" end></v-icon>
      </v-btn>
    </div>

    
    <div><h1>Temp</h1></div>
    
    <v-progress-circular :model-value="value" :rotate="360" :size="100" :width="15" color="teal">
      <template v-slot:default> {{ value }} % </template>
    </v-progress-circular>

    <input v-model="id" type="text">
    <button @click="add">CLICK</button>

    <h1>Humi</h1>
    <v-progress-circular :model-value="value1" :rotate="360" :size="100" :width="15" color="red">
      <template v-slot:default> {{ value1 }} % </template>
    </v-progress-circular>

    <!-- <input v-model="id" type="text">
    <button @click="add">CLICK</button> -->
  </div>
</template>

<script>
import mqtt from "mqtt";

export default {
  data() {
    return {
      id: 10,
      name: "hello",
      msg: "",
      sw: "",
      status: "",
      value: 12,
      value1: 60,
    };
  },
  
  created() {
    this.client = mqtt.connect("ws://broker.emqx.io:8083/mqtt");
    this.client.on("connect", this.onMqttConnect);
    this.client.on("message", this.onMqttMessage);
    this.client.on("reconnect", this.handleOnReConnect);
  },
  
  beforeDestroy() {
    this.client && this.client.end();
  },
  
  methods: {
    add() {
      this.value = this.id++;
      this.client.publish("room/sw01", String(this.value));
    },
    
    onMqttConnect() {
      this.status = "Mqtt connected";
      this.client.subscribe("status");
      this.client.subscribe("room/sw01");
    },
    
    onMqttMessage(topic, message) {
      if (topic === "status") {
        this.msg = message.toString();
      }
      if (topic === "room/sw01") {
        this.value = message.toString();
      }
    },
    
    handleOnReConnect() {
      // Handle reconnection logic
    }
  }
};
</script>
