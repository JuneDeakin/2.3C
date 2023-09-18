<template>
  <div>
    <h1>{{ title }}</h1>
    <div>
      <h2>Bird List</h2>
      <BirdItem v-for="(bird, index) in birdList" :key="index" :bird="bird" />
    </div>

    <div class="top-left">
      <p class="date">Today's Date: {{ formattedDate }}</p>
      <p class="date">Today's Day: {{ customFormattedDate }}</p>
    </div>
    <h2><i>Contact The Conservation</i></h2>
    <form @submit.prevent="validateForm">
      <label for="name">Name:</label>
      <input type="text" id="name" name="name" v-model="formData.name" required>
      <span class="error">{{ formErrors.name }}</span>
      <br><br>

      <label for="email">Email:</label>
      <input type="email" id="email" name="email" v-model="formData.email" required>
      <span class="error">{{ formErrors.email }}</span>
      <br><br>

      <label for="message">Message:</label>
      <textarea id="message" name="message" v-model="formData.message" required></textarea>
      <span class="error">{{ formErrors.message }}</span>
      <br><br>

      <input type="submit" value="Submit">
    </form>
  </div>
</template>

<script>
import moment from 'moment';
import BirdItem from './BirdItem.vue';

export default {
  components: {
    BirdItem
  },
  data() {
    return {
      title: 'Endangered Birds of NZ',
      headerColor: 'rgb(134, 198, 37)',
      currentDate: moment().toISOString(),
      formData: {
        name: '',
        email: '',
        message: ''
      },
      formErrors: {
        name: '',
        email: '',
        message: ''
      },
      uppercaseResult: '',
      substringResult: '',
      selectedCategory: '', // Selected category from dropdown
      categories: ['All', 'Habitat', 'Population', 'Behaviour'], // Available categories
      birdList: [
      { name: 'Kakapo', description: 'The kakapo is the only flightless parrot in the world.', path: 'kakapo' },
      { name: 'Takahe', description: 'The largest living rail in the world.', path: 'takahe' }
        // Add more bird data as needed
      ],
    };
  },
  computed: {
    formattedDate() {
      return moment(this.currentDate).format('MMMM Do YYYY, h:mm:ss a');
    },
    customFormattedDate() {
      return moment(this.currentDate).format('dddd');
    },
    kakapoUrl() {
      return '/kakapo';
    },
  },
  methods: {
    notifyParent() {
      this.$emit('child-event', 'Data to send to the parent');
    },
    validateForm() {
      // Validation logic here, similar to your validateForm function
      // Set formErrors appropriately
      // Return isValid

      // Example of updating data properties:
      this.uppercaseResult = "Title: " + this.formData.name.toUpperCase();
      this.substringResult = "Name: " + this.formData.name.substring(0, 7);
    },
    updatePopulationCount() {
      // Replace this with code to fetch the actual live population count
      // For now, we'll just use the initial value for demonstration
      this.populationCount = 247;
    },
    navigateToKakapo() {
      this.$router.push({ path: this.kakapoUrl });
    },
  },
};
</script>

<style scoped>
table {
  border-collapse: collapse;
  width: 100%;
}

th, td {
  border: 1px solid #ddd;
  padding: 8px;
  text-align: left;
}

/* Style the table header */
th {
  background-color: #f2f2f2;
}

.header-container {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding-bottom: 20px;
  border-bottom: 1px solid #ddd;
}

.image1 img {
  max-width: 50%;
  height: auto;
}

.center {
  text-align: center;
}

.top-left {
  position: absolute;
  top: 0;
  left: 0;
  background-color: lightblue;
  padding: 10px;
  border-bottom-right-radius: 10px;
}

.date {
  margin: 0;
  font-size: 14px;
}

.fact-container {
  text-align: center;
}
</style>

<style>
.video-container iframe {
  width: 100%;
  max-height: 30%;
}
.center-image {
  display: block;
  margin: 0 auto;
}
.form-group {
  margin-bottom: 20px;
}
body {
    text-align: center;
    font-family: 'Times New Roman', Times, serif;
    line-height: 1.5;
    padding: 20px;
    background-color: lightblue;
  }
.contact-form {
  text-align: left;
}
.header-text {
  margin: 0;
}
.contact-title {
  color: #777;
  margin: 0;
}
.fact-card {
  border: 1px solid #ddd;
  padding: 10px;
  margin: 10px 0;
  background-color: #f9f9f9;
  box-shadow: 0px 2px 4px rgba(0, 0, 0, 0.1);
}
</style>
