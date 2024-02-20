<template>
    <div class="h-screen bg-red-400 flex justify-center py-16">
        <div class="w-1/3">
            <div class="p-4 text-right shadow-2xl rounded-t-lg bg-white">
                <p class="font-semibold text-gray-700 h-6">
                    {{ getOperation }}
                </p>
                <p class="font-bold text-3xl text-gray-900 my-2">
                    {{ getResult }}
                </p>
            </div>

            <div class="grid grid-cols-4 grid-rows-5 shadow-2xl rounded-b-lg">
                <button class="h-16 text-xl text-white font-semibold bg-red-500 border-red-400 col-span-2 hover:bg-red-600" @click="clickAC()">
                    AC
                </button>
                <button class="h-16 text-xl text-white font-semibold bg-red-500 border-red-400 hover:bg-red-600" @click="clickDEL()">
                    DEL
                </button>
                <button class="h-16 text-xl text-white font-semibold bg-gray-700 border-gray-600 hover:bg-gray-800" @click="click('÷')">
                    ÷
                </button>


                <button class="h-16 text-xl text-white font-semibold bg-red-500 border-red-400 hover:bg-red-600" @click="click('7')">
                    7
                </button>
                <button class="h-16 text-xl text-white font-semibold bg-red-500 border-red-400 hover:bg-red-600" @click="click('8')">
                    8
                </button>
                <button class="h-16 text-xl text-white font-semibold bg-red-500 border-red-400 hover:bg-red-600" @click="click('9')">
                    9
                </button>
                <button class="h-16 text-xl text-white font-semibold bg-gray-700 border-gray-600 hover:bg-gray-800" @click="click('x')">
                    x
                </button>


                <button class="h-16 text-xl text-white font-semibold bg-red-500 border-red-400 hover:bg-red-600" @click="click('4')">
                    4
                </button>
                <button class="h-16 text-xl text-white font-semibold bg-red-500 border-red-400 hover:bg-red-600" @click="click('5')">
                    5
                </button>
                <button class="h-16 text-xl text-white font-semibold bg-red-500 border-red-400 hover:bg-red-600" @click="click('6')">
                    6
                </button>
                <button class="h-16 text-xl text-white font-semibold bg-gray-700 border-gray-600 hover:bg-gray-800" @click="click('-')">
                    -
                </button>


                <button class="h-16 text-xl text-white font-semibold bg-red-500 border-red-400 hover:bg-red-600" @click="click('1')">
                    1
                </button>
                <button class="h-16 text-xl text-white font-semibold bg-red-500 border-red-400 hover:bg-red-600" @click="click('2')">
                    2
                </button>
                <button class="h-16 text-xl text-white font-semibold bg-red-500 border-red-400 hover:bg-red-600" @click="click('3')">
                    3
                </button>
                <button class="h-16 text-xl text-white font-semibold bg-gray-700 border-gray-600 hover:bg-gray-800" @click="click('+')">
                    +
                </button>


                <button class="h-16 text-xl text-white font-semibold bg-red-500 border-red-400 col-span-2 hover:bg-red-600 rounded-bl-lg" @click="click('0')">
                    0
                </button>
                <button class="h-16 text-xl text-white font-semibold bg-red-500 border-red-400 hover:bg-red-600" @click="click('.')">
                    .
                </button>
                <button class="h-16 text-xl text-white font-semibold bg-gray-700 border-gray-600 hover:bg-gray-800 rounded-br-lg" @click="clickResult()">
                    =
                </button>
            </div>
        </div>
    </div>

</template>

<script>
export default {

    data () {
        return {
            getOperation: '',
            getResult: '0',
        }
    },

    methods: {
        clickAC() {
            this.getResult = '0'
        },
        clickDEL() {
            if(this.getResult.length > 1) {
                this.getResult=this.getResult.substring(0, this.getResult.length - 1);
            }
            else {
                this.getResult = '0';
            }
        },
        clickResult() {
            let operation = this.getResult;
            this.getOperation = operation;

            operation = operation.replace('x', '*');
            operation = operation.replace('÷', '/');
            
            this.getResult = eval(operation);
        },
        click(par) {
            if(this.getResult == '0') {
                this.getResult = par;
            }
            else {
                this.getResult += par;
            }
        }
    }

}
</script>

<style>

button {
    border: 1px solid;
}
</style>