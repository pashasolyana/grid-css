<template>
    <v-dialog v-model="dialog" max-width="600">
      <v-card>
        <v-card-title>
          <span class="headline">Добавить устройство</span>
          <v-spacer></v-spacer>
          <v-btn icon @click="close">
            <v-icon>mdi-close</v-icon>
          </v-btn>
        </v-card-title>
  
        <v-card-text>
          <p>Что добавляем?</p>
          <v-select
            :items="deviceOptions"
            label="Выберите устройство"
            v-model="selectedDevice"
            @change="fetchDeviceData"
          ></v-select>
          
          <v-text-field
            label="Укажите серийный номер"
            v-model="serialNumber"
          ></v-text-field>
  
          <v-text-field
            label="Укажите характеристики"
            v-model="characteristics"
          ></v-text-field>
        </v-card-text>
  
        <v-card-actions>
          <v-spacer></v-spacer>
          <v-btn color="green" @click="save">Сохранить</v-btn>
        </v-card-actions>
      </v-card>
    </v-dialog>
  
    <v-btn @click="open">Добавить устройство</v-btn>
  </template>
  
  <script>
  export default {
    data() {
      return {
        dialog: false,
        deviceOptions: [], // Здесь будут данные, полученные с сервера
        selectedDevice: null,
        serialNumber: '',
        characteristics: '',
      };
    },
    methods: {
      open() {
        this.dialog = true;
        this.fetchDeviceOptions(); // Заказ данных при открытии диалога
      },
      close() {
        this.dialog = false;
      },
      fetchDeviceOptions() {
        // Здесь вы должны написать логику для запроса данных с сервера
        // Например:
        // axios.get('/api/devices').then(response => {
        //   this.deviceOptions = response.data;
        // });
      },
      save() {
        // Логика для сохранения устройства
        console.log('Сохранить', this.selectedDevice, this.serialNumber, this.characteristics);
      }
    }
  };
  </script>
  
  <style scoped>
  .headline {
    font-weight: bold;
  }
  </style>
  