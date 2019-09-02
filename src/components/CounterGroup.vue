<template>
    <div class="counterGroup">
        <label><input type="number" v-model="counterNum" @input="countersInit"></label>
        <ol>
            <li>
                 <Counter v-for="n in getNumber(counterNum)" v-bind:key="n"
                          v-bind:index="n" v-bind:counter="counters[n-1]" v-on:update="numTotal"/>
            </li>
        </ol>
        <p class="number">sum:{{sum}}</p>
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
                sum:0
            }
        },

        methods:{
            isNumber(n){
                return !isNaN(parseInt(n)) && isFinite(n);
            },

            countersInit(){
                this.counters=[];
                if(this.isNumber(this.counterNum)){
                    for(let i=1; i<=this.counterNum; i++){
                        this.counters.push(i);
                    }
                }
                this.getSum();
            },

            getNumber(){
                if(this.isNumber(this.counterNum)){
                    return parseInt(this.counterNum);
                }else {
                    this.counterNum = 0;
                    this.sum = 0;
                    return this.counterNum;
                }
            },
            numTotal(data){
                this.counters[data.index-1] = data.value;
                this.getSum();
            },
            getSum(){
                this.sum = 0;
                for(let i=0; i<this.counters.length;i++){
                    this.sum+=this.counters[i];
                }
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
