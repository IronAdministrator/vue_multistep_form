<template>
  <form class="form-container">
    <section v-if="step == 1">
      <h1>First Step</h1>
      <div class="form-control">
        <label class="input-label">Name</label>
        <input type="text" v-model="form.name">
      </div>
      <div class="form-control">
        <label class="input-label">Surname</label>
        <input type="text" v-model="form.surname">
      </div>
    </section>

    <section v-if="step == 2">
      <h1>Second Step</h1>
      <div class="form-control">
        <label class="input-label">Username</label>
        <input type="text" v-model="form.username">
      </div>
    </section>

    <section v-if="step == 3">
      <h1>Third Step</h1>
      <div class="form-control">
        <label class="input-label">Email</label>
        <input type="email" v-model="form.email">
      </div>
      <div class="form-control">
        <label class="input-label">Phone Number</label>
        <input type="tel" v-model="form.tel">
      </div>
    </section>

    <section v-if="step == 4">
      <h1>Fourth Step</h1>
      <div class="newsletter-container">
        <input type="checkbox" name="newsletter" v-model="form.newsletter">
        <p>Do you want to receive our Newsletter?</p>
      </div>
    </section>

    <div class="btn-container">
      <button class="prev-btn" v-if="step != 1" @click.prevent="prevStep">Previous</button>
      <button class="next-btn" v-if="step != totalSteps" @click.prevent="nextStep">Next</button>
    </div>
  </form>

  <p>name: {{ form.name }}</p>
  <p>surname: {{ form.surname }}</p>

</template>

<script>

export default {
  name: 'App',
  components: {
    
  },
  data() {
    return {
      step: 1,
      totalSteps: 4,
      form: {
        name: '',
        surname: '',
        username: '',
        email: null,
        tel: null,
        newsletter: false
      }
    }
  },
  methods: {
    prevStep() {
      this.step--
    },
    nextStep() {
      this.step++
    }
  }
}
</script>

<style>
*, *:before, *:after {
  box-sizing: border-box;
}
body {
  background: #2c3e50;
}
#app {
  height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: white;
}

.form-container {
  width: 60%;
  background: rgb(46, 55, 85);
  color: white;
  border-radius: 1rem;
  padding: 2rem;
}
.form-control {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  margin-bottom: 1rem;
}
input {
  font-size: 1.35rem;
  outline: 0;
  background: transparent;
  box-shadow: none;
  border: none;
  border-bottom: 2px dashed #DF5C2E;
  color: white;
}
.newsletter-container {
  display: flex;
  flex-direction: row;
  justify-content: center;
  align-items: center;
}
input[type=checkbox] {
  margin-inline: .8rem;
}
.btn-container {
  display: flex;
  justify-content: space-between;
}
.next-btn {
  margin-left: auto;
}
</style>