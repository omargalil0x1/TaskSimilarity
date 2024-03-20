<template>
  <div class="main-form-container">
    <div class="form-inputs">
      <div class="group-1-field">
        <h2> Input One <span v-show="firstNull" class="firstField-error-feedback"> Can't be empty </span> </h2>

        <textarea ref="first_text_field" v-model="firstText" rows="16" class="input-field" placeholder="Paste Your First Input Here!"></textarea>
      </div>
      <div class="d-flex" style="height: 100%;">
        <div class="vr"></div>
      </div>
      <div class="group-2-field">
        <h2> Input Two <span v-show="secondNull" class="secondField-error-feedback"> Can't be empty </span> </h2>
        <textarea ref="second_text_field" v-model="secondText" rows="16" class="input-field" placeholder="Paste Your First Input Here!">

        </textarea>
      </div>
    </div>
    <div class="form-button-compare">
      <button @click="sendData" id="compare-button" class="btn btn-success"> Compare </button>
    </div>
  </div>
</template>

<script>
  export default {
    data: function() {
      return {
        firstText: '',
        secondText: '',
        firstNull: false,
        secondNull: false,
      }
    },
    methods: {
      sendData() {
        if(this.firstText == '' && this.secondText == '') {
          this.firstNull = true;
          this.secondNull = true;

        } else if(this.secondText == '') {
          this.firstNull = false;
          this.secondNull = true;

        } else if(this.firstText == '') {
          this.secondNull = false;
          this.firstNull = true;

        } else if(this.firstText != '' && this.secondText == '') {
          this.firstNull = false;
          this.secondNull = true;

        } else if(this.firstText == '' && this.secondText != '') {
          this.firstNull = true;
          this.secondNull = false;
        }
        else if (this.firstText != '' && this.secondText != ''){
          this.firstNull = false;
          this.secondNull = false;
          this.$emit('data_sent', this.firstText, this.secondText);
        }
      }
    }
  }
</script>





<style scoped>

  .main-form-container {
    color: white;
    width: 60%;
    margin: auto;
    margin-top: 25px;
    display: flex;
    flex-direction: column;
    background-color: rgba(0, 0, 0, 0.5);
    border: 1px solid rgba(0, 0, 0, 0.4);
    border-radius: 10px;
    padding: 10px;
    transition: 0.2s;
  }

  .form-button-compare {
    width: 90%;
    margin-top: 10px;
    border-top: 1px solid rgba(255, 255, 255, 0.6);
    align-items: center;
    justify-content: center;
    display: flex;
    padding: 10px;
    margin: auto
  }

  .form-inputs {
    display: flex;
    flex-direction: row;
  }

  .main-form-container:hover {
    border: 1px solid rgba(0, 0, 0, 0.2);
    background-color: rgba(255, 255, 255, 0.3);
    cursor: pointer;
  }

  .group-1-field, .group-2-field, .input-field {
    width: 100%;
  }

  .vr {
    margin-left: 5px;
    margin-right: 5px;
  }

  .input-field {
    border: none;
    border-radius: 9px;
    padding: 8px;
  }

  .input-field:focus {
    outline: 2px solid rgba(0, 100, 0, 1);
  }

  .firstField-error-feedback {
    font-size: 16px;
    color: rgb(210, 0, 0);
    font-weight: bold;
    margin-left: 15px;
    background-color: rgba(200, 0, 0, 0.3);
    border-radius: 11px;
    padding: 10px;
  }

  .secondField-error-feedback {
    font-size: 16px;
    color: rgb(210, 0, 0);
    font-weight: bold;
    margin-left: 15px;
    background-color: rgba(200, 0, 0, 0.3);
    border-radius: 11px;
    padding: 10px;
  }

</style>
