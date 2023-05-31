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
    <aside>

        <div class="flex items-center justify-start gap-2">
            <div class="w-2 h-2 mt-0.5 bg-green-500 animate-pulse rounded-full"></div>
            <h2 class="font-black text-xl">
                Food Orders
            </h2>
        </div>

        <div class="mt-8 grid grid-cols-1 gap-8">
            <div
                v-for="order in orderList"
                class="flex items-center justify-start gap-x-4"
            >
                <div class="w-16 h-16 overflow-hidden rounded-full">
                    <img class="object-center object-cover w-full h-full" alt="foodPic" :src="order.foodImage" />
                </div>

                <div class="flex flex-col gap-y-2 flex-grow">
                    <p class="font-bold text-lg">
                        {{ order.foodName }}
                    </p>
                
                    <div class="flex items-center justify-between">
                        
                        <div class="flex items-center justify-between gap-x-1">
                            <p class="text-slate-500">
                                ${{ order.foodPrice }}
                            </p>

                            <p class="text-slate-500">
                                x{{ order.count }}
                            </p>
                        </div>

                        <div class="font-bold text-lg">
                            ${{ order.foodPrice * order.count }}
                        </div>
                    </div>
                </div>
            </div>
        </div>

        <div v-if="orderList.length > 0" class="flex items-center justify-between mt-8">
            <p class="font-black text-xl text-slate-700">
                Total Price
            </p>
            
            <p class="font-black text-xl">
                ${{ totalPrice }}
            </p>
        </div>

        <div v-else>
            <p class="font-black text-xl text-slate-300 text-center">
                Made your day with a food!
            </p>
        </div>

    </aside>
</template>