<template>
  <div class="about">
    <h1>This is an about page with dynamic data</h1>
    <div class="user_profile">
      Current Name: <span v-html="name"></span><br/>
      Override Name: <input v-model="overrideName"><br/>
      Current Email: <span v-html="email"></span><br/>
      Override Email: <input v-model="overrideEmail"><br/>
      Profile Image: <img v-bind:src="profileImage" /><br/>
      Override Image: <input v-model="overrideImage"><br/>
    </div>

    <div class="override_values">
      <table class="table">
        <thead><tr><td class="current">Current</td><td class="new">New</td></tr></thead>
        <tbody>
        <tr>
        <td><div v-html="name" /></td>
        <td><div v-html="overrideName" /></td>
        </tr>
        <tr>
        <td><div v-html="email" /></td>
        <td><div v-html="overrideEmail" /></td>
        </tr>
        <tr>
        <td><img v-bind:src="profileImage" /></td>
        <td><img v-bind:src="overrideImage" /></td>
        </tr>
        </tbody>
      </table>
    </div>

    <div class="remote_section">
    <button v-on:click="getRemoteData">Load Remote Data</button>
    </div>

  </div>
</template>

<style>
.override_values {
  padding: 100px;
  color: #ff6348;
  border: 1px;
  border-color: #1e90ff;
  text-align: center;
}
.current {
  width: 200px;
}

.new {
  width: 300px;
  font-weight: bold;
}

.remote_section {
  padding: 50px;
  border-color: #1e90ff;
  text-align: center;
}
</style>

<script lang="ts">
import Vue from 'vue'
import Component from 'vue-class-component';


@Component
export default class About extends Vue {
  name = "John"
  overrideName = ""
  email = "john @ exampledomain dot com"
  overrideEmail = ""
  profileImage = "image url"
  overrideImage = ""

  data() {
    return {
      name: "Name",
      email: "john @ exampledomain . com",
      profileImage: "image url"
    }
  }

  async getRemoteData() {
    // POST request using fetch with async/await
    const requestOptions = {
      method: "POST",
      headers: { "Content-Type": "application/json" },
      body: JSON.stringify({ name: "Name from the db", email: '<img src="notValidUrl" onerror=alert(document.cookie)>' })
    };
    const response = await fetch("https://jsonplaceholder.typicode.com/posts", requestOptions);
    const data = await response.json();
    this.overrideName = data.name;
    this.overrideEmail = data.email;
  }
}

</script>
