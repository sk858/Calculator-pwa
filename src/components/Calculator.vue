<template>
    <v-app id='calculator'>
        <v-content>
            <v-container>
                <v-alert v-model="formulaAlert" dismissible type="error">Invalid Formula</v-alert>
                <v-text-field clearable v-model="formula"></v-text-field>
                <v-btn @click="evaluate()">=</v-btn>
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
    }
  }
};
</script>

<style scoped>
</style>
