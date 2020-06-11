<template id="main">
    <v-ons-page>
        <v-ons-toolbar>
            <div class="center">Add min and max</div>
        </v-ons-toolbar>
        <v-ons-list-item class="margin-top-3">
            <div class="center">
                <input placeholder="min" float
                             v-model="minNumber"
                             type="number"
                             min="0"
                             max="10"
                             v-on:input="$emit('changefbdfb', $event.target)"
                >
            </div>
        </v-ons-list-item>
        <v-ons-list-item>
            <div class="center">
                <v-ons-input placeholder="max" float
                             v-model="maxNumber"
                             type="number"
                             min="0"
                             max="10"
                >
                </v-ons-input>
            </div>
        </v-ons-list-item>
        <v-ons-list-item>
            <div class="right">
                Your Number {{ rundomNumber || ' will be here' }}!
            </div>
        </v-ons-list-item>
        <section style="margin: 16px">
            <v-ons-button
                    modifier="large"
                    style="margin: 6px 0px"
                    v-on:click="getNumber">Get result</v-ons-button>
        </section>

        <v-ons-fab
                position="bottom right"
                :visible="fabVisible"
        >
            <v-ons-icon icon="md-face"></v-ons-icon>
        </v-ons-fab>
    </v-ons-page>
</template>

<div id="app"></div>

<script>


    export default {
        name: 'App',
        data() {
            return {
                fabVisible: true,
                minNumber: 0,
                maxNumber: 10,
                rundomNumber: 5,
                minValuesss: 1,
                maxValue: 10,
            }
        },
        watch: {
            minNumber(a) {
                this.minNumber = a;
                this.validateMinNumber(a);
            },
            maxNumber(b) {
                this.maxNumber = b;
                this.validateMaxNumber(b);
            }
        },
        methods: {
            changefbdfb(tamara) {
                console.log('tamara' + tamara);
            },
            getNumber: function() {
                let min = Number(this.minNumber);
                let max = Number(this.maxNumber);
                this.rundomNumber = (Math.floor(Math.random() * (max - min + 1)) + min);
                return this.rundomNumber;
            },
            validateMinNumber: function(a) {
                let min = Number(a);
                let max = Number(this.maxNumber);

                if(min < max && min > this.minValuesss){
                    this.minNumber = min;
                }else {
                    this.minNumber = 0;
                    console.log('ufter thisminNumber' + this.minNumber);
                }
                return this.minNumber;

            },
            validateMaxNumber: function(b) {

                let maxdd = Number(b);
                let minValuesss = this.minNumber;

                if (maxdd < this.maxValue && maxdd > minValuesss) {
                        maxdd;
                }else{
                    maxdd = 10;
                    this.maxNumber = 10;
                    console.log('ufter maxdd wrong' + maxdd);
                    console.log('ufter thismaxNumber wrong' + this.maxNumber);
                }
                return this.maxNumber;


            }
        },

    }
</script>

<style>
    #app {
        font-family: Avenir, Helvetica, Arial, sans-serif;
        -webkit-font-smoothing: antialiased;
        -moz-osx-font-smoothing: grayscale;
        text-align: center;
        color: #2c3e50;
        margin-top: 60px;
    }
    .margin-top-3 {
      margin-top: 3vh;
    }
</style>
