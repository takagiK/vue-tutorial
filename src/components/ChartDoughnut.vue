<script>
import { Doughnut, mixins } from "vue-chartjs";
const { reactiveProp } = mixins

export default {
    extends: Doughnut,
    mixins: [reactiveProp],
    props: ['charData', 'options'],
    mounted() {
        this.renderChart( this.chartData );
    }
};
</script>