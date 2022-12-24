<script setup>
import { ref } from 'vue';
import mermaid from 'mermaid';

// attributes
let mermaid_svg = ref('');

// props
const props = defineProps({
    chart_code: String
});

// expose
defineExpose({
    render_mermaid
})

function render_mermaid() {
    mermaid.render(
        'what',
        props.chart_code, 
        (svgCode) => {
            mermaid_svg.value = svgCode;
        }
    );
}

</script>

<template>
<div class="mermaid-chart"
    v-html="mermaid_svg">
</div>
</template>