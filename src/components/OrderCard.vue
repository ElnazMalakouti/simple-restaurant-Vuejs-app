<script setup>
defineProps({
    orderList: {
        type: Array,
        requierd: true
    },
    totalPrice: {
        type: Number
    },
    addOrderFunction: {
        type: Function
    },
    removeOrderFunction: {
        type: Function
    }
})
</script>


<template>
    <div class="w-[400px] bg-[#F0F8FF] p-[16px] rounded-[16px] flex flex-col gap-[16px] justify-start items-center">

        <div class="w-full flex justify-start items-center">
            <p>Your order list:</p>
        </div>

        <div class="w-full min-h-[100px] max-h-[252px] px-[16px] overflow-auto">

            <div class="w-full flex flex-col gap-[4px]">
                <div class="w-full p-[12px] bg-white rounded-[8px] flex flex-col justify-between items-start"
                    v-for="order in orderList">
                    <div>
                        <p class="text-[22px]">{{ order.foodName }}</p>
                    </div>
                    <div class="w-full flex justify-between items-end text-[18px]">
                        <p>{{ order.foodPrice }}$</p>
                        <div class="flex justify-center items-center gap-[8px]">
                            <button :disabled="order.count === 0 ? true : false"
                                class="w-[26px] h-[26px] bg-[#9E1010] text-white text-[24px] font-bold rounded-tl-[4px] rounded-bl-[4px] border flex justify-center items-center disabled:bg-[#D1D5DB] disabled:text-[#6B7280]">-</button>
                            <p>{{ order.count }}</p>
                            <button
                                class="w-[26px] h-[26px] bg-[#9E1010] text-white text-[22px] font-bold rounded-tr-[4px] rounded-br-[4px] border flex justify-center items-center">+</button>
                        </div>
                    </div>
                </div>
            </div>

        </div>

        <div class="mt-auto ml-[50%] text-[22px] font-bold flex justify-start items-center gap-[16px]">
            <p>Total Price:</p>
            <p>{{ totalPrice }}$</p>
        </div>

    </div>
</template>