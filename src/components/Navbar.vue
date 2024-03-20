<template>
  <div class="main-navbar-body">
    <div class="main-navbar-logo">
      Text Similarity Calculator
    </div>
    <div class="main-navbar-elements">
      <div @click="activate" ref="element_1" :class="{activated_element: active}" data-bs-toggle="collapse" data-bs-target="#collapseExample">
        How Does It Work?
      </div>
      <div @click="activate2" ref="element_2" :class="{activated_element2: active2}" data-bs-toggle="collapse" data-bs-target="#collapseExample2">
        How To Use It
      </div>
    </div>
  </div>

  <div class="about-us-block">
    <div class="about-us-block-content collapse" id="collapseExample">
      <p>
        Ever wondered how similar two pieces of text are?
        Our comparison tool takes the guesswork out by analyzing the content and providing a clear percentage score.
      </p>
      <h3> Here's the magic behind it: </h3>
      <ul>
        <li> Upload or Paste Your Texts: Simply upload two documents or paste your text directly into the designated fields. </li>
        <li> Advanced Text Analysis: Our tool breaks down both texts into individual elements like words, sentences, and structure. </li>
        <li> Intelligent Comparison: We compare these elements across both texts, identifying matches and highlighting differences. </li>
        <li> Similarity Score Revealed: Based on the analysis, you'll receive a clear percentage score indicating the overall similarity between the two texts. </li>
      </ul>
    </div>
  </div>

  <div class="about-us-block">
    <div class="about-us-block-content collapse" id="collapseExample2">
      <h3> How To Use It? </h3>
      <ul>
        <li> 1-Copy and Paste Your Text in (Input One) </li>
        <li> 2-Copy and Paste Your Text in (Input Two) </li>
        <li> 3-Click On 'Compare' </li>
        <li> 4-You Will Get Similarity Precentage Between Two Texts </li>
      </ul>
    </div>
  </div>
</template>

<script>
  export default {
    data: function() {
      return {
        active: false,
        active2: false,
      }
    },
    methods: {
      activate() {
        this.active = !this.active
        this.active ? this.$refs.element_2.style.pointerEvents = 'none' : this.$refs.element_2.style.pointerEvents = "all"
      },
      activate2() {
        this.active2 = !this.active2
        this.active2 ? this.$refs.element_1.style.pointerEvents = 'none' : this.$refs.element_1.style.pointerEvents = "all"

      }
    }
  }
</script>


<style scoped>
  .main-navbar-body {
    background-color: black;
    display: flex;
    flex-direction: row;
    color: white;
    font-family: sans-serif;
  }

  .main-navbar-logo {
    border-right: 1px solid rgba(255, 255, 255, 0.4);
    padding: 10px;
    transition: 0.2s;
  }

  .main-navbar-logo:hover {
    border-bottom: 6px solid lightsalmon;
    cursor: pointer;
  }

  .main-navbar-elements {
    display: flex;
    flex-direction: row;
  }

  .main-navbar-elements > div {
    transition: 0.3s;
    padding: 10px;
  }

  .main-navbar-elements > div:hover {
    background-color: rgba(255, 255, 255, 0.4);
    cursor: pointer;
  }

  .about-us-block {
    position: relative;
    display: inline-block;
  }

  .about-us-block-content {
    position: absolute;
    text-align: left;
    border: 1px solid rgba(0, 0, 0, 0.5);
    border-top-left-radius: 0px;
    border-bottom-right-radius: 25px;
    border-top-right-radius: 11px;
    padding: 10px;
    width: 50%;
    background-color: #ffb676;
    font-family: sans-serif;
  }

  .activated_element {
    color: lightblue;
    border-bottom: 2px solid lightblue;
  }

  .activated_element {
    color: lightblue;
    border-bottom: 2px solid lightblue;
  }

  .activated_element2 {
    color: lightblue;
    border-bottom: 2px solid lightblue;
  }
</style>
