<template>
  <form @submit.prevent="submitForm">
    <div
      class="form-control"
      :class="{ invalid: userNameValidity === 'invalid' }"
    >
      <label for="user-name">Your Name</label>
      <input
        @blur="validateInput"
        id="user-name"
        name="user-name"
        type="text"
        v-model.trim="userName"
      />
      <p v-if="userNameValidity === 'invalid'">Please enter a valid name</p>
    </div>
    <div class="form-control">
      <label for="age">Your Age (Years)</label>
      <input
        ref="ageInput"
        v-model="userAge"
        id="age"
        name="age"
        type="number"
      />
    </div>
    <div class="form-control">
      <label for="referrer">How did you hear about us?</label>
      <select id="referrer" name="referrer" v-model="referrer">
        <option value="google">Google</option>
        <option value="wom">Word of mouth</option>
        <option value="newspaper">Newspaper</option>
      </select>
    </div>
    <div class="form-control">
      <h2>What are you interested in?</h2>
      <div>
        <input
          id="interest-news"
          name="interest"
          type="checkbox"
          value="news"
          v-model="interest"
        />
        <label for="interest-news">News</label>
      </div>
      <div>
        <input
          v-model="interest"
          id="interest-tutorials"
          name="interest"
          type="checkbox"
          value="tutorials"
        />
        <label for="interest-tutorials">Tutorials</label>
      </div>
      <div>
        <input
          v-model="interest"
          id="interest-nothing"
          name="interest"
          type="checkbox"
          value="nothing"
        />
        <label for="interest-nothing">Nothing</label>
      </div>
    </div>
    <div class="form-control">
      <h2>How do you learn?</h2>
      <div>
        <input
          value="video"
          id="how-video"
          name="how"
          type="radio"
          v-model="how"
        />
        <label for="how-video">Video Courses</label>
      </div>
      <div>
        <input
          value="blogs"
          v-model="how"
          id="how-blogs"
          name="how"
          type="radio"
        />
        <label for="how-blogs">Blogs</label>
      </div>
      <div>
        <input
          value="other"
          v-model="how"
          id="how-other"
          name="how"
          type="radio"
        />
        <label for="how-other">Other</label>
      </div>
    </div>
    <div class="form-control">
      <rating-control v-model="rating"></rating-control>
    </div>
    <div class="form-control">
      <input
        v-model="confirm"
        type="checkbox"
        id="confirm-terms"
        name="confirm-terms"
      />
      <label for="confirm-terms">Agree to terms of use?</label>
    </div>
    <div>
      <button>Save Data</button>
    </div>
  </form>
</template>

<script>
import RatingControl from './RatingControl.vue';
export default {
  components: {
    'rating-control': RatingControl,
  },
  data() {
    return {
      userName: '',
      userAge: null,
      referrer: 'wom',
      interest: [],
      how: null,
      confirm: false,
      userNameValidity: 'pending',
      rating: null,
    };
  },
  methods: {
    submitForm() {
      console.log('username: ' + this.userName);
      this.userName = '';
      console.log('User age:');
      console.log(this.userAge + 5);
      console.log(this.$refs.ageInput.value + 5);
      console.log(31);
      this.userAge = null;
      console.log('Referrer: ' + this.referrer);
      this.referrer = 'wom';
      console.log('Checkboxes?');
      console.log(this.interest);
      this.interest = null;
      console.log('Radio Buttons?');
      console.log(this.how);
      console.log((this.how = null));
      console.log('confirm?');
      console.log(this.confirm);
      this.confirm = false;
      console.log('Rating:');
      console.log(this.rating);
      this.rating = null;
    },
    validateInput() {
      if (this.userName === '') {
        this.userNameValidity = 'invalid';
      } else {
        this.userNameValidity = 'valid';
      }
    },
  },
};
</script>

<style scoped>
form {
  margin: 2rem auto;
  max-width: 40rem;
  border-radius: 12px;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.26);
  padding: 2rem;
  background-color: #ffffff;
}

.form-control {
  margin: 0.5rem 0;
}

label {
  font-weight: bold;
}

h2 {
  font-size: 1rem;
  margin: 0.5rem 0;
}

input,
select {
  display: block;
  width: 100%;
  font: inherit;
  margin-top: 0.5rem;
}

select {
  width: auto;
}

input[type='checkbox'],
input[type='radio'] {
  display: inline-block;
  width: auto;
  margin-right: 1rem;
}

input[type='checkbox'] + label,
input[type='radio'] + label {
  font-weight: normal;
}

button {
  font: inherit;
  border: 1px solid #0076bb;
  background-color: #0076bb;
  color: white;
  cursor: pointer;
  padding: 0.75rem 2rem;
  border-radius: 30px;
}

button:hover,
button:active {
  border-color: #002350;
  background-color: #002350;
}

.form-control.invalid input {
  border-color: red;
}
.form-control.invalid label {
  color: red;
}
</style>
