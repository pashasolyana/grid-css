<template>
  <div>
    <div class="employee-container" v-for="(employeeData, index) in data" :key="index">
      <div class="table-container">
        <div class="employee-info">
          <div>
            <span class="employee-name">{{ employeeData.employee.name }}</span><br>
            <span class="employee-position">{{ employeeData.employee.position }}</span>
          </div>
          <v-btn class="add-device-btn" color="green" @click="openModal(employeeData)" dark>+ Добавить устройство</v-btn>
        </div>
        <div class="table">
          <div class="header">Предмет</div>
          <div class="header">Инв. номер</div>
          <div class="header">Железо</div>
          <div class="header">Когда добавлена/изменена</div>

          <div v-for="(item, itemIndex) in employeeData.items" :key="itemIndex" class="table-row">
            <div class="row">{{ item.name }}</div>
            <div class="row">{{ item.invNumber }}</div>
            <div class="row">{{ item.hardware }}</div>
            <div class="row">{{ item.addedDate }} / {{ item.modifiedDate }}</div>
          </div>
        </div>
      </div>
    </div>

    <!-- Модальное окно -->
    <v-dialog v-model="dialog" max-width="600px">
      <v-card>
        <v-card-title>
          <span>Добавить устройство</span>
        </v-card-title>
        <v-card-text>
          <v-text-field v-model="newDevice.name" label="Предмет"></v-text-field>
          <v-text-field v-model="newDevice.invNumber" label="Инв. номер"></v-text-field>
          <v-text-field v-model="newDevice.hardware" label="Железо"></v-text-field>
        </v-card-text>
        <v-card-actions>
          <v-btn color="green" @click="addDevice">Добавить</v-btn>
          <v-btn @click="dialog = false">Отмена</v-btn>
        </v-card-actions>
      </v-card>
    </v-dialog>
  </div>
</template>

<script>
export default {
  name: 'EmployeeTable',
  props: {
    data: {
      type: Array,
      required: true
    }
  },
  data() {
    return {
      dialog: false,
      newDevice: {
        name: '',
        invNumber: '',
        hardware: ''
      },
      selectedEmployee: null
    };
  },
  methods: {
    openModal(employeeData) {
      this.selectedEmployee = employeeData; // сохраняем выбранного сотрудника
      this.dialog = true; // открываем модальное окно
    },
    addDevice() {
      if (this.selectedEmployee) {
        // Добавляем новое устройство в массив items выбранного сотрудника
        this.selectedEmployee.items.push({
          name: this.newDevice.name,
          invNumber: this.newDevice.invNumber,
          hardware: this.newDevice.hardware,
          addedDate: new Date().toLocaleDateString(), // Устанавливаем текущую дату как дату добавления
          modifiedDate: new Date().toLocaleDateString() // Подобно для даты изменения
        });
        this.dialog = false; // Закрываем модальное окно
        this.resetNewDevice(); // Сбрасываем данные нового устройства
      }
    },
    resetNewDevice() {
      this.newDevice.name = '';
      this.newDevice.invNumber = '';
      this.newDevice.hardware = '';
    }
  },
};
</script>

<style scoped>
.employee-container {
  margin-bottom: 32px;
}

.table-container {
  display: grid;
  grid-template-columns: auto 1fr;
  gap: 16px;
  padding: 16px;
  border: 1px solid #ccc;
  border-radius: 8px;
}

.employee-info {
  display: grid;
  grid-template-rows: auto auto;
  align-items: center;
  gap: 16px;
  padding: 16px;
  background-color: #f5f5f5;
  border-right: 1px solid #ccc;
}
.employee-name {
  font-weight: bold;
  font-size: 18px;
}

.employee-position {
  font-size: 14px;
  color: #666;
}

.add-device-btn {
  white-space: nowrap;
  align-self: start;
}

.table {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  gap: 8px;
  align-items: start;
}

.header {
  font-weight: bold;
  background-color: #e0e0e0;
  padding: 8px;
  text-align: center;
}

.table-row {
  display: contents;
}

.row {
  background-color: #fff;
  padding: 8px;
  text-align: center;
}
</style>