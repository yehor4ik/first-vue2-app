<template>
  <div class="hello">
    <div class="holder">
      <form @submit.prevent="addSkill">
        <input type="text" placeholder="Enter a skill you have..." v-model="skill" v-validate="'min:5'" name="skill">

        <transition name="alert-in" enter-active-class="animated flipInX" leave-active-class="animated flipOutX">
          <p class="alert" v-if="errors.has('skill')">{{ errors.first('skill') }}</p>
        </transition>
      </form>
      <ul>
        <transition-group enter-active-class="animated bounceInUp" leave-active-class="animated bounceOutDown">
          <li v-for="(data, idx) in skills" :key="idx">
            {{ data.skill }}
            <i class="bi bi-x-circle" v-on:click="remove(idx)"></i>
          </li>
        </transition-group>
      </ul>

      <p>There are the skills that you process.</p>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Skills',
  data() {
    return {
      skill: '',
      skills: [
        {"skill": 'Vue.js'},
        {"skill": 'Frontend Developer'},
      ],
    }
  },
  methods: {
    addSkill() {
      this.$validator.validateAll().then((result) => {
        if(result) {
          this.skills.push({skill: this.skill});
          this.skill = '';
        } else {
          console.warn('Not valid')
        }
      })
    },
    remove(id) {
      this.skills.splice(id, 1);
    }
  }
}
</script>

<style scoped>
@import 'https://cdnjs.cloudflare.com/ajax/libs/animate.css/3.5.1/animate.min.css';
@import "https://cdn.jsdelivr.net/npm/bootstrap-icons@1.11.2/font/bootstrap-icons.min.css";

.holder {
  background-color: #fff;
}

ul {
  margin: 0;
  padding: 0;
  list-style-type: none;
}

ul li {
  padding: 20px;
  font-size: 1.3em;
  background-color: #e0edf4;
  border-left: 5px solid #3eb3f6;
  margin-bottom: 2px;
  color: #3e5252;
}

p {
  text-align: center;
  padding: 30px 0;
  color: gray;
}

.container {
  box-shadow: 0 0 40px lightgray;
}

input {
  width: calc(100% - 40px);
  border: 0;
  padding: 20px;
  font-size: 1.3em;
  background-color: #323333;
  color: #687f7f;
}

.alert {
  background-color: #fdf2ce;
  font-weight: bold;
  display: block;
  padding: 5px;
  margin: 0;
}

.alert-in-enter-active {
  animation: bounse-in .5s;
}
.alert-in-leave-active {
  animation: bounse-in .5s reverse;
}

@keyframes bounse-in {
  0% {
    transform: scale(0);
  }
  50% {
    transform: scale(1.5);
  }
  100% {
    transform: scale(1);
  }
}

i {
  float: right;
  cursor: pointer;
}
</style>
