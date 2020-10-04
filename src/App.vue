<template>
  <div class="container">
    <h3>Exercise (Inputs)</h3>
    <hr />
    <div class="row">
      <div class="col-md-6">
        <div class="panel panel-warning">
          <div class="panel-heading">
            <h4>Application Form</h4>
          </div>
          <div class="panel-body">
            <form>
              <div class="row">
                <div class="col-md-12">
                  <div class="form-group">
                    <label for="email">User Name</label>
                    <input
                      type="text"
                      id="username"
                      v-model="userData.username"
                      class="form-control"
                    />
                  </div>
                  <div class="form-group">
                    <label for="password">Password</label>
                    <input
                      type="password"
                      id="password"
                      v-model.lazy.number.trim="userData.password"
                      class="form-control"
                    />
                  </div>
                  <div class="form-group">
                    <label for="age">Age</label>
                    <input
                      type="number"
                      id="age"
                      v-model.number.trim="userData.age"
                      class="form-control"
                    />
                  </div>
                </div>
              </div>
              <div class="row">
                <div class="col-md-12 form-group">
                  <label for="message">Message</label><br />
                  <textarea
                    id="message"
                    rows="3"
                    v-model="userData.message"
                    class="form-control"
                  ></textarea>
                </div>
              </div>
              <div class="row">
                <div class="col-md-12">
                  <div class="form-group">
                    <label>
                      <input
                        v-model="userData.interests"
                        type="checkbox"
                        value="software"
                      />
                      Software
                    </label>
                    <label>
                      <input
                        v-model="userData.interests"
                        type="checkbox"
                        value="hardware"
                      />Hardware
                    </label>
                  </div>
                </div>
              </div>
              <div class="row">
                <div class="col-md-12 form-group">
                  <label>
                    <input
                      v-model="userData.gender"
                      type="radio"
                      value="male"
                    />
                    Male
                  </label>
                  <label>
                    <input
                      v-model="userData.gender"
                      type="radio"
                      value="female"
                    />
                    Female
                  </label>
                </div>
              </div>
              <div class="row">
                <div class="col-md-12 from-group">
                  <label>City</label>
                  <select v-model="userData.selectedCity" class="form-control">
                    <option v-for="city in userData.cities" :key="city">{{
                      city
                    }}</option>
                  </select>
                </div>
              </div>
              <hr />
              <div class="row">
                <div class="col-md-12">
                  <button @click.prevent="submit" class="btn btn-primary">
                    Send!
                  </button>
                </div>
              </div>
            </form>
          </div>
        </div>
      </div>
      <div class="col-md-6" v-if="isSubmitted">
        <div class="panel panel-info">
          <div class="panel-heading">
            <h4>Form Data</h4>
          </div>
          <div class="panel-body">
            <p>User Name: {{ userData.username }}</p>
            <p>Password: {{ userData.password }}</p>
            <p>Age: {{ userData.age }}</p>
            <p style="white-space: pre;">Message: {{ userData.message }}</p>
            <p><strong>Interests</strong></p>
            <ul>
              <li v-for="item in userData.interests" :key="item">{{ item }}</li>
            </ul>
            <p>Sex: {{ userData.gender }}</p>
            <p>City: {{ userData.selectedCity }}</p>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      userData: {
        username: "",
        password: "",
        age: 30,
        message: "",
        interests: [],
        gender: "",
        cities: ["Lisboa", "Braga", "Faro", "Porto", "Coimbra"],
        selectedCity: "Porto",
      },
      isSubmitted: false,
    };
  },
  methods: {
    submit() {
      this.isSubmitted = true;
    },
  },
};
</script>
