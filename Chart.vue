<script>
import axios from 'axios';
import { Line } from 'vue-chartjs';

const url = 'http://0.0.0.0:7777/jk'

export default {
    extends: Line,
    data(){ 
        return {
            gdp_list:[],
            year_list:[],
            info:[],
            headers: {'Access-Control-Allow-Origin': '*'}
        } 
    },
    mounted () {
        axios
        .get(url,this.headers)
        .then(response => {
            this.info = response["data"]//responseデータを絞り込む
            for (var item in this.info) {
                this.gdp_list.push(this.info[item]["gdp"])
                this.year_list.push(this.info[item]["year"])
            }
        }),

        this.renderChart({
            labels: this.year_list,
            datasets: [{
                label: 'Data-Chart',
                backgroundColor: '#f87979',
                data: this.gdp_list,
            }],
            options: {
                responsive: false,
                scales: {
                    // display: true,
                    yAxes: [{
                        ticks: {
                            beginAtZero: true, //開始値を0
                            min: 0, //最小値
                        }
                    }]
                }
            }
        })
    }
}
</script>