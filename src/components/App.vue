<template>
  <div class="app-template">
      <h3>My Identicon Generator</h3>
      <div>
          Input:
          <input v-on:input="onInput" />
      </div>
      <div>
          Output: <div class="output">{{ reversal }}</div> <!-- REVERSAL ONLY HERE TO SHOW WHAT CAN BE PUT IN CURLY BRACES -->
          <div v-html="identicon"></div>
      </div>
  </div>
</template>

<script>
export default {
    data: function() {
        return {
            textInput: ''
        }
    },
    computed: {
        identicon: function() {
            return jdenticon.toSvg(this.textInput, 300);
        },
        // random computed function to show what can be inserted into HTML using the double curly brackets
        reversal: function() {
            return this.textInput.split('').reverse().join('');
        }
    },
    methods: {
        onInput: function(event) {
            this.textInput = event.target.value;
        }
    }
}
</script>

<style scoped>

    div {
        font-size: 1em;
        font-family: 'Gill Sans';
    }

    .app-template {
        text-align: center;
    }

    h3 {
        font-size: 2em;
        margin: 20px;
    }

    .output {
        display: inline-block;
        width: 120px;
    }

</style>
