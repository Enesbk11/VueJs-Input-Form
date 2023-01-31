<template>
  <div class="container">
    <h3>Form Input</h3>
    <hr>
    <div class="row">
      <div class="col-md-6">
        <div class="panel panel-danger">
          <div class="panel-heading">
            <h4>Form Input</h4>
          </div>
          <div class="panel-body">
            <form>
              <div class="row">
                <div class="col-md-12">
                  <div class="form-group">
                    <label for="email">User Name</label>
                    <input type="text" id="username" class="form-control" v-model="userData.username">
                  </div>
                  <div class="form-group">
                    <label for="password">Password</label>
                    <input type="password" class="form-control" id="password" v-model.lazy.trim="userData.password">
                  </div>
                  <div class="form-group">
                    <label for="age">Age</label>
                    <input type="number" id="age" class="form-control" v-model.number.trim="userData.age">
                  </div>
                </div>
              </div>
              <div class="row">
                <div class="col-md-12 form-group">
                  <label for="message">Descriptions</label><br>
                  <textarea v-model="userData.message" id="message" rows="3" class="form-control"></textarea>
                </div>
              </div>
              <div class="row">
                <div class="col-md-12">
                  <div class="form-group">
                    <label for="skills">Skills</label>
                    <hr>
                    <label>
                      <input v-model="userData.interests" type="checkbox" value="Software"> Software
                    </label>
                    <br>
                    <label>
                      <input v-model="userData.interests" type="checkbox" value="Hardware"> Hardware
                    </label>
                    <br>
                    <label>
                      <input v-model="userData.interests" type="checkbox" value="Java"> Java
                    </label>
                    <br>
                    <label>
                      <input v-model="userData.interests" type="checkbox" value="DevOps"> DevOps
                    </label>
                    <br>
                    <label>
                      <input v-model="userData.interests" type="checkbox" value="Vue Js"> Vue Js
                    </label>
                  </div>

                </div>
              </div>
              <div class="row">
                <div class="col-md-12 form-group">
                  <label style="margin-top: 2rem;">Gender</label>
                  <hr>
                  <label>
                    <input v-model="userData.gender" type="radio" value="Male"> Male
                  </label>
                  <br>
                  <label>
                    <input v-model="userData.gender" type="radio" value="Female"> Female
                  </label>
                </div>
              </div>
              <div class="row">
                <div class="col-md-12 from-group">
                  <label>City</label>
                  <select v-model="userData.selectedCity" class="form-control">
                    <option :selected="city == 'Adana'" v-for="city in userData.cities"> {{ city }}</option>
                  </select>
                </div>
              </div>
              <div class="row">
                <div class="col-md-12 form-group">
                  <app-switch v-model="switched"></app-switch>
                </div>
              </div>
              <hr>
              <div class="row">
                <div class="col-md-12">
                  <button @click.prevent="submit" class="btn btn-warning">Send!
                  </button>
                </div>
              </div>
            </form>
          </div>
        </div>
      </div>
      <div id="form-data" class="col-md-6" v-if="isSubmitted">
        <div class="panel panel-info">
          <div class="panel-heading">
            <h4>Form Data</h4>
          </div>
          <div class="panel-body">
            <label for="">Username
              <p>{{ userData.username }}</p>
            </label>
            <hr>
            <label for="">Password
              <p>{{ userData.password }}</p>
            </label>
            <hr>
            <label for="">Age
              <p>{{ userData.age }}</p>
            </label>
            <hr>
            <label for="">Descriptions
              <p style="white-space: pre;">{{ userData.message }}</p>
            </label>
            <hr>
            <label for="">Skills
              <ul>
                <li v-for="item in userData.interests"> {{ item }}</li>
              </ul>
            </label>
            <hr>
            <label for="">Gender
              <p>{{ userData.gender }}</p>
            </label>
            <hr>
            <label for="">City
              <p>{{ userData.selectedCity }}</p>
            </label>
          </div>
        </div>
      </div>
    </div>

  </div>
</template>

<script>


export default {
  components: {

  },
  data() {
    return {
      userData: {
        username: '',
        password: '',
        age: null,
        message: '',
        interests: [],
        gender: '',
        cities: ["İstanbul", "Ankara", "Adana", "İzmir", "Elazığ", "Diyarbakır", "Bursa", "Konya", "Trabzon"],
        selectedCity: ''
      },
      
      isSubmitted: false
    }
  },
  methods: {
    submit() {
      this.isSubmitted = true;
    }
  }
}
</script>

<style >
body {
  background-color: #F0F8FF;
}
</style>
