<template>
    <div class="counterGroup">
        <label><input type="number" v-model="counterNum" @input="countersInit"></label>
        <ol>
            <li>
                 <Counter v-for="n in getNumber(counterNum)"
                          v-bind:key="n"
                          v-bind:index="n"
                          v-bind:counter="counters[n-1]"
                          v-on:update="updateCounters"/>
            </li>
        </ol>
        <p class="number">sum:{{getSum()}}</p>
    </div>
</template>



<script>
    import Counter from './Counter.vue'
    export default {
        name: 'counterGroup',
        components: {
            Counter
        },

        data(){
            return{
                counterNum: 0,
                counters:[],
            }
        },

        methods:{
            isNumber(n){
                return !isNaN(parseInt(n)) && isFinite(n);
            },

            countersInit(){
                let counterNum = this.getNumber();
                while(counterNum > this.counters.length){
                    this.counters.push(this.counters.length+1)
                }
                while(counterNum < this.counters.length){
                    this.counters.pop();
                }
                this.getSum();
            },

            getNumber(){
                if(this.isNumber(this.counterNum)){
                    return parseInt(this.counterNum);
                }else {
                    this.counterNum = 0;
                    this.getSum();
                    return this.counterNum;
                }
            },

            updateCounters(data){
                let oldCounters = this.counters;
                oldCounters[data.index-1] = data.value;
                this.counters = [];
                for(let i=0; i<oldCounters.length; i++){
                    this.counters.push(oldCounters[i]);
                }
                this.getSum();
            },

            getSum(){
                let sum = 0;
                for(let i=0; i<this.counters.length;i++){
                    sum+=this.counters[i];
                }
                return sum;
            }
        }

    }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
    h3 {
        margin: 40px 0 0;
    }
    ul {
        list-style-type: none;
        padding: 0;
    }
    li {
        display: inline-block;
        margin: 0 10px;
    }
    a {
        color: #42b983;
    }
    .number{
        font-size:30px;
        color: olivedrab;
    }

</style>
