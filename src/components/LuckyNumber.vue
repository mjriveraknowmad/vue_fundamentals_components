<template>
    <div class="float-end">
        <button class="btn btn-outline-danger" @click="generateLuckyNumber()">
            <span v-if="luckyNumber === 0">Generate Lucky Number <br />
                Range(1-{{ maxNumber }})</span>
            <span v-else>Lucky Number: {{ luckyNumber }} <br />
                Click to generate new lucky number</span>
        </button>
    </div>
</template>
<script setup lang="ts">
import { inject, ref, type Ref } from "vue";
let luckyNumber = ref(0);

// const props = defineProps({
//     maxNumber: { type: Number, default: 100 },
// });
const maxNumber: Ref | undefined = inject("maxNumber");

function generateLuckyNumber() {
    if (maxNumber) {
        luckyNumber.value = Math.floor(Math.random() * maxNumber.value);
        console.log(maxNumber.value, luckyNumber.value);
    }
}
</script>
