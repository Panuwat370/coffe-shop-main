<template>
  <div id="app">
  <!-- เฮดเดอร์ -->
  <header>
    <h1>My Cafe</h1>
  </header>

  <main class="container mx-auto p-4">
    <div id='1' class="grid grid-cols-2 gap-4">
      <div v-for="(cafe, index) in cafes" :key="index" class="bg-white p-4 border rounded-lg">
        <h2 class="text-xl">{{ cafe.name }}</h2>
        <p>{{ cafe.description }}</p>
        <img :src="cafe.image" alt="" width="200" height="200"><br>
        <button @click="reserveTable(index)" class="bg-primary text-white px-2 py-1 mt-2">จองโต๊ะ</button>
      </div>
    </div>
  </main>

  <!-- ส่วนแสดงผลรายละเอียดการจอง -->
  <section v-if="reservation" class="container mx-auto p-4">
    <h2 class="text-2xl mb-4">รายละเอียดการจอง</h2>
    <div class="bg-white p-4 border rounded-lg">
      <div>
        <strong>ชื่อ:</strong> {{ reservation.name }}
      </div>
      <div>
        <strong>เบอร์โทร:</strong> {{ reservation.phone }}
      </div>
      <div>
        <strong>วันที่:</strong> {{ reservation.date }}
      </div>
      <div>
        <strong>เวลา:</strong> {{ reservation.time }}
      </div>
      <div>
        <strong>จำนวนโต๊ะ:</strong> {{ reservation.tableCount }}
      </div>
    </div>
  </section>
</div>
</template>

<script>
import { ref } from 'vue';

export default {
setup() {
  const cafes = ref([
    {
      name: 'U Forests Cafe',
      description: 'U Forests Cafe ร้านกาแฟน้ำตกสุดอลังการ.',
      image: 'https://s.isanook.com/tr/0/ui/287/1438251/1757538.jpg'
    },
    {
      name: 'Petit Peyton Traveloque Cafe',
      description: 'Petit Peyton Traveloque Cafe (พิถีพิถัน คาเฟ่) คาเฟ่ย้อนยุค .',
      image: 'https://www.gourmetandcuisine.com/Images/editor_upload/_editor20210719022633_original.jpg'
    },
    {
      name: 'EL CAFE',
      description: 'El Cafe คาเฟ่มินิมอล วิวพาโนรามา.',
      image: 'https://www.japaikin.com/wp-content/uploads/2021/06/ElCafe-Khaoyai-01.jpg'
    }
  ]);

  const reservation = ref(null);

  function reserveTable(index) {
    const name = prompt('ชื่อผู้จอง:');
    const phone = prompt('เบอร์โทรศัพท์:');
    const date = prompt('วันที่:');
    const time = prompt('เวลา:');
    const tableCount = prompt('จำนวนโต๊ะ:');

    setReservation({ name, phone, date, time, tableCount });
  }

  function setReservation(data) {
    reservation.value = data;
  }

  return {
    cafes,
    reservation,
    reserveTable,
  };
},
};
</script>


<style>
/* เฮดเดอร์ */
header {
background-color: #333;
color: #a08080;
text-align: center;
padding: 1rem 0;
}

header h1 {
margin: 0;
}

</style>
