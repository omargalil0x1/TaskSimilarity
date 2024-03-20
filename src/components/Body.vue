<template>
  <div class="main-body-container">
    <Form @data_sent="compareData"/>
  </div>
  <div class="slider-thumb"> </div>

  <teleport to="#modal-container">
    <!-- Button trigger modal -->
    <button ref="modal_activation" style="display: none" type="button" class="btn btn-primary" data-bs-toggle="modal" data-bs-target="#exampleModal"> </button>

    <!-- Modal -->
    <div class="modal fade" id="exampleModal" tabindex="-1" aria-labelledby="exampleModalLabel" aria-hidden="true">
      <div class="modal-dialog">
        <div class="modal-content">
          <div class="modal-header">
            <h1 class="modal-title fs-5" id="exampleModalLabel">Comparison Results </h1>
            <button type="button" class="btn-close" data-bs-dismiss="modal" aria-label="Close"></button>
          </div>
          <div class="modal-body">
            Similarity : <span ref="perc_span" style="display: inline-block"> {{ precentage }}% </span>
          </div>
          <div class="modal-footer">
            <button type="button" class="btn btn-secondary" data-bs-dismiss="modal">Close</button>
          </div>
        </div>
      </div>
    </div>

  </teleport>
</template>

<script>
  import Form from './BodyComponents/Form.vue'

  export default {
    components: { Form },
    data: function() {
      return {
        precentage: 0,
      }
    },
    methods: {
      compareData(firstText, secondText) {

          fetch(`https://text-similarity-calculator.p.rapidapi.com/stringcalculator.php?ftext=${firstText}&stext=${secondText}`, {
            method: "GET",
            headers: {
              'X-RapidAPI-Key': '4739c3afeamsh44d08ccd88f95cap1fe21fjsn30d590215208',
              'X-RapidAPI-Host': 'text-similarity-calculator.p.rapidapi.com'
            }
          })
          .then(response => {
            return response.text() // this will pass the value to the next 'then'
          })
          .then(text => {
            this.precentage = JSON.parse(text).percentage
            this.$refs.modal_activation.click()
            this.$refs.perc_span.style.color = `hsl(${this.precentage}, 100%, 50%)`
          })
          .catch(error => {
            console.log(error)
          })
      }
    }
  }
</script>

<style scoped>
  .main-body-container {
    display: flex;
    flex-direction: column;
    width: 100%;
  }

  .modal-body {
    font-size: 24px;
    font-family: sans-serif;
    font-weight: bold;
    margin: auto;
  }
</style>
