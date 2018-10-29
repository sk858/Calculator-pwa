<template>
    <v-app id='calculator'>
        <v-content>
            <v-container fluid justify-center align-center>
                <v-layout row wrap justify-center fill-height>
                    <v-text-field box color="orange" clearable v-model="formula"></v-text-field>
                    <v-btn large color="red" @click="append(null)">C</v-btn>
                </v-layout>
                <v-layout row wrap justify-center>
                  
                      <v-btn large outline color="grey" @click="append(7)">7</v-btn>
                      <v-btn large outline color="grey" @click="append(8)">8</v-btn>
                      <v-btn large outline color="grey" @click="append(9)">9</v-btn>
                      <v-btn large color="grey" @click="append('/')">/</v-btn>
                 
                </v-layout>
                <v-layout row wrap justify-center>
                  
                      <v-btn large outline color="grey" @click="append(4)">4</v-btn>
                      <v-btn large outline color="grey" @click="append(5)">5</v-btn>
                      <v-btn large outline color="grey" @click="append(6)">6</v-btn>
                      <v-btn large color="grey" @click="append('*')">*</v-btn>
                 
                </v-layout>
                <v-layout row wrap justify-center>
                  
                      <v-btn large outline color="grey" @click="append(1)">1</v-btn>
                      <v-btn large outline color="grey" @click="append(2)">2</v-btn>
                      <v-btn large outline color="grey" @click="append(3)">3</v-btn>
                      <v-btn large color="grey" @click="append('-')">-</v-btn>
                 
                </v-layout>
                <v-layout row wrap justify-center>
                  
                      <v-btn large outline color="grey" @click="append(0)">0</v-btn>
                      <v-btn large color="blue" @click="evaluate()">=</v-btn>
                      <v-btn large color="grey" @click="append('.')">.</v-btn>
                      <v-btn large color="grey" @click="append('+')">+</v-btn>
                  
                </v-layout>
                <v-alert v-model="formulaAlert" dismissible type="error">Invalid Formula</v-alert>
            </v-container>
        </v-content>
    </v-app>
</template>

<script>
export default {
  data() {
    return {
      formula: "",
      formulaAlert: false
    };
  },
  methods: {
    evaluate() {
      try {
        /* WARNING! Never use eval in production code. */
        let result = eval(this.formula);
        this.formulaAlert = false;
        this.formula = result;
      } catch (exception) {
        this.formulaAlert = true;
      }
    },
    append(val){
      if(val==null){
        this.formula="";
      }else{
        this.formula+=val;
      }
    }
  }
};
</script>

<style scoped>

.container{
  width:470px;
  border-style: solid;
  margin-top:100px;
}
.v-text-field{
  
  height:59px;
  display:inline-block;
  margin-top: 0;
  margin-bottom:0;
}
</style>
