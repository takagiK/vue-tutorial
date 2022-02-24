<script>
import { Bubble, mixins } from "vue-chartjs";
const { reactiveProp } = mixins

export default {
    extends: Bubble,
    mixins: [reactiveProp],
    props: ['charData', 'options'],
    mounted() {
        this.renderChart( this.chartData );
    }
};
</script>