<template>
    <div>
        <div class="w-full flex justify-center mt-8">
            <div class="bg-white shadow-md rounded px-8 pt-6 pb-8 mb-4">
                <div class="mb-4">
                    <input v-model.number="inp1"
                           placeholder="Number 1"
                           class="shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline">
                </div>
                <div class="relative inline-block w-full text-gray-700 mb-4">
                    <select v-model="symbol"
                            class="w-full h-10 pl-3 pr-6 text-base shadow placeholder-gray-600 border rounded appearance-none focus:shadow-outline">
                        <option value="+" selected> + </option>
                        <option value="-"> - </option>
                        <option value="*"> * </option>
                        <option value="/"> / </option>
                    </select>
                    <div class="absolute inset-y-0 right-0 flex items-center px-2 pointer-events-none">
                        <svg class="w-4 h-4 fill-current" viewBox="0 0 20 20"><path d="M5.293 7.293a1 1 0 011.414 0L10 10.586l3.293-3.293a1 1 0 111.414 1.414l-4 4a1 1 0 01-1.414 0l-4-4a1 1 0 010-1.414z" clip-rule="evenodd" fill-rule="evenodd"></path></svg>
                    </div>
                </div>
                <div class="mb-6">
                    <input v-model.number="inp2"
                           placeholder="Number 2"
                           class="shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline">
                </div>
                <div class="flex items-center justify-center">
                    Total sum: <span v-if="!isNaN(totalSum)" :class="totalSum > 0 ? 'text-green-500' : 'text-red-500'">{{ totalSum }}</span>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
export default {
  name: 'Calculation',
  data: () => {
    return {
      inp1: 0,
      inp2: 0,
      symbol: '+'
    }
  },
  computed: {
    totalSum () {
      switch (this.symbol) {
        case '+':
          return this.inp1 + this.inp2
        case '-':
          return this.inp1 - this.inp2
        case '*':
          return this.inp1 * this.inp2
        case '/':
          return this.inp1 / this.inp2
      }
      return false
    }
  }
}
</script>
