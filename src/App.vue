<script >
import './assets/main.css'
import FoodCard from './components/FoodCard.vue'
import OrderCard from './components/OrderCard.vue'
export default {
  components: {
    FoodCard,
    OrderCard
  },
  data() {
    return {
      foodList: [
        {
          foodId: 1,
          foodName: 'Pasta Alfredo',
          foodPrice: 23,
          foodImage: '/pics/alfredo.jpg',
          count: 0
        },
        {
          foodId: 2,
          foodName: 'Fried Chicken',
          foodPrice: 45,
          foodImage: '/pics/fried chicken.jpg',
          count: 0
        },
        {
          foodId: 3,
          foodName: 'Burgur',
          foodPrice: 33,
          foodImage: '/pics/burger.jpg',
          count: 0
        },
        {
          foodId: 4,
          foodName: 'French Fries',
          foodPrice: 27,
          foodImage: '/pics/french fries.jpg',
          count: 0
        },
        {
          foodId: 5,
          foodName: 'Coca Cola',
          foodPrice: 10,
          foodImage: '/pics/coca.jpg',
          count: 0
        },
        {
          foodId: 6,
          foodName: 'Pepperoni',
          foodPrice: 40,
          foodImage: '/pics/pepperoni.jpg',
          count: 0
        },
      ],
      orderList: [],
      totalPrice: 0
    }
  },
  methods: {
    addFoodOrder(id) {
      const temp = this.orderList.find(item => item.foodId === id)

      if (temp) {
        temp.count = temp.count + 1
      } else {
        const food = this.foodList.find(item => item.foodId === id)
        this.orderList.push({
          foodId: id,
          foodName: food.foodName,
          foodPrice: food.foodPrice,
          count: 1
        })
      }

      this.totalPrice = 0
      for (const item of this.orderList) {
        this.totalPrice = this.totalPrice + (item.foodPrice * item.count);
      }
      
    },
    removeFoodOrder(id) {
      const temp = this.orderList.find(item => item.foodId === id)

      if (temp) {
        if (temp.count < 2) {
          this.orderList = this.orderList.filter(item => item.foodId !== id)
        } else {
          temp.count = temp.count - 1          
        }
      }

      this.totalPrice = this.totalPrice - temp.foodPrice
    }
  }
}
</script>

<template >
  <div class="w-auto h-auto bg-[#F0F8FF] p-[24px] rounded-[16px] grid grid-cols-2 auto-rows-auto gap-[24px] ">
    <div class="flex justify-center items-center" v-for="food in foodList">
      <FoodCard :food-id="food.foodId" :food-name="food.foodName" :food-image="food.foodImage"
        :food-price="food.foodPrice" :count="food.count" :add-order-function="addFoodOrder"
        :remove-order-function="removeFoodOrder" />
    </div>
  </div>
  <OrderCard :orderList="this.orderList" :total-price="this.totalPrice" :add-order-function="addFoodOrder"
    :remove-order-function="removeFoodOrder" />
</template>

<style scoped></style>
