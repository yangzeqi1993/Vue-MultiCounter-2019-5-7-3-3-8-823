<template>
    <div class="counter">
        <h1>{{ msg }}</h1>
        <span>{{index}}:</span>
        <button type="button" class="leftButton" v-on:click="_add">+</button>
        <span id="number">{{counter}}</span>
        <button type="button" class="rightButton" v-on:click="_minus">-</button>
    </div>
</template>

<script>
    export default {
        name: 'Counter',
        props: {
            msg: String,
            index:Number,
            counter:Number
        },


        methods:{
            _add: function (){
                let addNum = 1;
                this.returnCounter(addNum);
            },

            _minus: function (){
                let minusNum = -1;
                this.returnCounter(minusNum);
            },

            returnCounter(num){
                this.$emit('update',
                    {
                        index: this.index,
                        value: this.counter + num
                      }
                );
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
    #number{
        font-size:30px;
        color: deeppink;
    }
    .leftButton{
        font-size:20px;
        margin-right: 80px
    }
    .rightButton{
        font-size:20px;
        margin-left: 80px
    }

</style>
