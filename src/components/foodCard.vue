<script setup>
import 'tailwindcss/tailwind.css'
defineProps({
    foodId: {
        type: Number,
        required: true
    },
    foodName: {
        type: String,
        required: true
    },
    foodPrice: {
        type: Number,
        required: true
    },
    foodImage: {
        type: String,
        required: true
    },
    count: {
        type: Number,
        required: true
    },
    addOrderFunction : {
        type : Function
    },
    removeOrderFunction : {
        type : Function
    }
})
</script>

<template>
    <div class="w-[350px] h-[120px] bg-white p-[16px] rounded-[8px] flex gap-[16px] justify-start items-center">


        <div class="w-[95px] h-[95px] rounded-[50%]">
            <img class="w-full h-full rounded-[50%]" alt="foodPic" :src="foodImage" />
        </div>

        <div class="w-[65%] h-full py-[8px] flex flex-col justify-between items-start">
            <div>
                <p class="text-[22px]">{{ foodName }}</p>
            </div>
            <div class="w-full flex justify-between items-end text-[18px]">
                <p>{{ foodPrice }}$</p>
                <div class="flex justify-center items-center gap-[8px]">
                    <button @click="() => {
                        count--
                        removeOrderFunction(this.foodId)
                        }" 
                        :disabled="count === 0 ? true : false" 
                        class="w-[26px] h-[26px] bg-[#9E1010] text-white text-[24px] font-bold rounded-tl-[4px] rounded-bl-[4px] border flex justify-center items-center disabled:bg-[#D1D5DB] disabled:text-[#6B7280]">
                        -
                    </button>
                    <p>{{ count }}</p>
                    <button 
                    @click="() => {
                        count++
                        addOrderFunction(this.foodId)
                    }" 
                    class="w-[26px] h-[26px] bg-[#9E1010] text-white text-[22px] font-bold rounded-tr-[4px] rounded-br-[4px] border flex justify-center items-center">
                    +
                </button>
                </div>
            </div>
        </div>


    </div>
</template>


<style scoped></style>