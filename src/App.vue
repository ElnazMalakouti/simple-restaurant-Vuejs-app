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
        count: 0,
        description: 'Creamy pasta with Alfredo sauce'
      },
      {
        foodId: 2,
        foodName: 'Fried Chicken',
        foodPrice: 45,
        foodImage: '/pics/fried-chicken.jpg',
        count: 0,
        description: 'Crispy, flavorful fried chicken'
      },
      {
        foodId: 3,
        foodName: 'Chicken Salad',
        foodPrice: 33,
        foodImage: '/pics/chicken-salad.png',
        count: 0,
        description: 'Classic salad with juicy chicken'
      },
      {
        foodId: 4,
        foodName: 'Royal Meat Dish',
        foodPrice: 27,
        foodImage: '/pics/meat.png',
        count: 0,
        description: 'Crispy fries & royal meat'
      },
      {
        foodId: 5,
        foodName: 'Organic Dish',
        foodPrice: 10,
        foodImage: '/pics/organic-dish.png',
        count: 0,
        description: 'Healthy organic vegan dish'
      },
      {
        foodId: 6,
        foodName: 'Glory Steak',
        foodPrice: 40,
        foodImage: '/pics/stake-dish.png',
        count: 0,
        description: 'Juicy and flavorful steak with a glorious presentation'
      }
      ],
      orderList: [],
      totalPrice: 0
    }
  },
  methods: {
    addFoodOrder(id) {
      const temp = this.orderList.find(item => item.foodId === id)

      if (temp)
      {
        temp.count = temp.count + 1
      }
      else
      {
        const food = this.foodList.find(item => item.foodId === id)
        this.orderList.push({
          foodId: id,
          foodName: food.foodName,
          foodImage: food.foodImage,
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

<template>
  <main class="w-full h-screen  grid grid-cols-12 vb">

    <div class="py-24 px-16 col-span-9">
        <div class="grid grid-cols-4 gap-x-24 gap-y-24">
          <FoodCard
                v-for="food in foodList"
                :food-id="food.foodId"
                :food-name="food.foodName"
                :food-image="food.foodImage"
                :food-price="food.foodPrice"
                :food-description="food.description"
                :count="food.count"
                :add-order-function="addFoodOrder"
                :remove-order-function="removeFoodOrder"
              />
        </div>
    </div>

    <div class="bg-white col-span-3 border border-r border-slate-100 px-16 py-12">
      <OrderCard 
        :orderList="this.orderList"
        :total-price="this.totalPrice"
        :add-order-function="addFoodOrder"
        :remove-order-function="removeFoodOrder"
      />
    </div>

  </main>
</template>
