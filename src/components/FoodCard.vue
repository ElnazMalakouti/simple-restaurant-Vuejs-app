<script >
export default {
    props: {
        foodId: {
            type: Number,
            required: true
        },
        foodName: {
            type: String,
            required: true
        },
        foodDescription: {
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
        addOrderFunction: {
            type: Function
        },
        removeOrderFunction: {
            type: Function
        }
    }
}
</script>

<template>
    <div class="bg-white rounded-xl flex flex-col items-center justify-start relative">

        <div class="w-32 h-32 absolute -top-16">
            <div class="relative flex items-center justify-center">
                <img class="rounded-full overflow-hidden object-center object-cover absolute w-32 h-32 z-20 top-0"
                    alt="foodPic" :src="foodImage" />
                <img class="rounded-full overflow-hidden object-center object-cover absolute w-24 h-24 z-10 top-12 blur-lg"
                    alt="foodPic" :src="foodImage" />

            </div>
        </div>

        <div class="mt-24 mb-4 w-full flex flex-col px-6 h-full justify-between">
            <h6 class="font-bold text-xl text-center">
                {{ foodName }}
            </h6>

            <p class="text-slate-500 text-center mt-2">
                {{ foodDescription }}
            </p>

            <div class="flex items-center justify-between mt-8">
                <p class="font-bold text-3xl">
                    ${{ foodPrice }}
                </p>

                <div class="flex items-center justify-between gap-x-4">
                    <button 
                        @click="() => {
                            count--
                            removeOrderFunction(this.foodId)
                        }"
                        :disabled="count <= 0"
                        class="w-8 h-8 bg-rose-500 rounded-l text-white font-bold text-2xl hover:scale-90 transition-all duration-500 hover:bg-red-400
                        disabled:bg-slate-300 disabled:hover:scale-100"
                    >
                        -
                    </button>

                    <p class="font-mono">
                        {{ count }}
                    </p>
                    
                    <button 
                        @click="() => {
                            count++
                            addOrderFunction(this.foodId)
                        }"
                        :disabled="count >= 9"
                        class="w-8 h-8 bg-rose-500 rounded-r text-white font-bold text-2xl hover:scale-90 transition-all duration-500 hover:bg-red-400
                        disabled:bg-slate-300 disabled:hover:scale-100"
                    >
                        +
                    </button>
                </div>
            </div>
        </div>
    </div>
</template>
