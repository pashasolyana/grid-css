<template>
  <v-app>
    <v-main>
      <employee-table :data="data" />
    </v-main>
  </v-app>
</template>

<script>
import EmployeeTable from './components/EmployeeTable.vue';

export default {
  components: {
    EmployeeTable
  },
  data() {
    return {
      data: [
        {
          employee: {
            name: "Прудникова И.И.",
            position: "Начальник отдела"
          },
          items: [
            {
              name: "Компьютер",
              invNumber: "1232",
              hardware: "Intel Core i3-12100F OEM, MSI PRO B760M-E DDR4, KFA2 GeForce GTX 1650 X Black, Patriot Viper Elite II 16 ГБ, 256 ГБ SSD M.2 накопитель, ARDOR GAMING Ally AL1282",
              addedDate: "07.03.2023",
              modifiedDate: "07.03.2023"
            },
            {
              name: "Монитор",
              invNumber: "K32432",
              hardware: "ASUS K7-315",
              addedDate: "07.03.2023",
              modifiedDate: "07.03.2023"
            },
            {
              name: "Клавиатура и мышь",
              invNumber: "-",
              hardware: "Микрософт и микрософт",
              addedDate: "07.03.2023",
              modifiedDate: "07.03.2023"
            },
            {
              name: "Принтер",
              invNumber: "23432",
              hardware: "HP 1204KT",
              addedDate: "07.03.2023",
              modifiedDate: "07.03.2023"
            }
          ]
        },
        {
          employee: {
            name: "Иванов И.И.",
            position: "Менеджер"
          },
          items: [
            {
              name: "Ноутбук",
              invNumber: "5678",
              hardware: "Intel Core i5-10210U, 8GB RAM, 512GB SSD, NVIDIA MX250",
              addedDate: "07.03.2023",
              modifiedDate: "07.03.2023"
            },
            {
              name: "Монитор",
              invNumber: "A6789",
              hardware: "Dell 24' FHD",
              addedDate: "07.03.2023",
              modifiedDate: "07.03.2023"
            }
          ]
        }
      ]
    };
  }
};
</script>

<style>

html, body, #app {
  height: 100%;
  margin: 0;
}
</style>
