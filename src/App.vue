<template>
  <div>

    <nav class="menu">
      <ul>
        <li @click="resetReservation">หน้าหลัก</li>
        <li v-if="selectedCoffeeShop">เลือกร้าน: {{ selectedCoffeeShop.name }}</li>
      </ul>
    </nav>

    <CoffeeShopList :coffeeShops="coffeeShops" @reserve="reserveCoffeeShop" />

    <ReservationForm v-if="selectedCoffeeShop" @reserve="reserveCoffeeShop" />

    <div v-if="reservation" class="reservation-details">
      <h2>ข้อมูลการจอง</h2>
      <p><strong>ร้านคาเฟ่:</strong> {{ reservation.coffeeShopName }}</p>
      <p><strong>ชื่อ:</strong> {{ reservation.name }}</p>
      <p><strong>วันและเวลา:</strong> {{ reservation.datetime }}</p>
      <p><strong>เบอร์โทรศัพท์:</strong> {{ reservation.dataphone }}</p>
      <p><strong>จำนวนโต๊ะ:</strong> {{ reservation.tableCount }}</p>
    </div>
  </div>
</template>

<script>
import CoffeeShopList from './components/CoffeeShopList.vue';
import ReservationForm from './components/ReservationForm.vue';

export default {
  data() {
    return {
      coffeeShops: [
        { id: 1, name: 'ชานมคาเฟ่', available: true, image: 'https://www.gourmetandcuisine.com/Images/editor_upload/_editor20220622025109_original.jpg' },
        { id: 2, name: 'มูเลาะห์คาเฟ่', available: true, image: 'https://bluemochateas.com/wp-content/uploads/2022/07/ออกแบบร้านกาแฟเล็กๆ.jpg.webp' },
        { id: 3, name: 'ร้านบ้านเพื่อน', available: true, image: 'https://www.funnymandesign.com/2007/wp-content/uploads/2021/09/milk-tea-shop-design_01.jpg' },
        { id: 4, name: 'อร่อยเลิศคาเฟ่', available: true, image: 'https://i.pinimg.com/736x/a9/e5/7f/a9e57f09d42fc7ddc68d701043c0c629.jpg' },
      ],
      selectedCoffeeShop: null,
      reservation: null,
    };
  },
  components: {
    CoffeeShopList,
    ReservationForm,
  },
  methods: {
    reserveCoffeeShop(reservation) {
      this.reservation = reservation;
    },
    resetReservation() {
      this.selectedCoffeeShop = null;
      this.reservation = null;
    },
  },
};
</script>

<style scoped>

body {
  font-family: Arial, sans-serif;
  margin: 0;
  padding: 0;
  background-color: #f5f5f5;
}


header {
  background-color: #6b5b2c;
  color: #f7f7f7;
  text-align: center;
  padding: 1rem;
  margin-bottom: 1rem;
}


.menu {
  background-color: #4C3D21;
  color: #f7f7f7;
  text-align: center;
  padding: 0.5rem;
}

.menu ul {
  list-style: none;
  padding: 0;
}

.menu li {
  display: inline;
  margin-right: 1rem;
  cursor: pointer;
}

.menu li:last-child {
  margin-right: 0;
}


.coffee-shop-list {
  margin-bottom: 1rem;
}


.reservation-details {
  background-color: #000000;
  padding: 1rem;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
  border-radius: 4px;
  margin-top: 1rem;
}


.coffee-shop-info {
  display: flex;
  align-items: center;
  margin-bottom: 1rem;
}

.coffee-shop-info img {
  width: 50px;
  height: 50px;
  margin-right: 1rem;
}


button {
  background-color: #493e1c;
  color: #f7f7f7;
  border: none;
  padding: 5px 10px;
  margin: 5px;
  cursor: pointer;
  border-radius: 4px;
}

button:hover {
  background-color: #4C3D21;
}
</style>

