<template>
    <div id="app">
        <div class="chart">
            <Chart></Chart>
        </div>
    </div>
</template>

<script>
// Ajax通信ライブラリ
import Chart from './Chart';

export default({
    el:'#app',
    components: {
        Chart
    }
})
</script>

<style scoped>
/* .chart{
    width:600px;
    height:600px;
} */
</style>