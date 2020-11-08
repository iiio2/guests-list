<template>
  <div class="container">
    <div class="row">
      <div class="col-sm-8">
        <form @submit.prevent="submitForm">
          <input
            v-model="guest"
            class="form-control"
            placeholder="Guest Name"
            name="form"
          />
          <br />
          <input
            class="btn btn-sm btn-success"
            type="submit"
            value="Add Guest"
          />
        </form>
        <div class="progress">
          <div
            :style="{ width: guestsCapacityPercentage + '%' }"
            class="length"
          ></div>
        </div>
      </div>
      <div class="col-sm-4">
        <ul>
          <li :key="guest" v-for="guest in guests">{{ guest }}</li>
        </ul>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data: function() {
    return {
      guest: "",
      guests: [],
      guestsCapacity: 10,
      guestsCapacityPercentage: 0
    };
  },
  methods: {
    submitForm: function() {
      if (
        this.guest.trim().length > 0 &&
        this.guestsCapacityPercentage === 100
      ) {
        alert("Not allowed more than 10 guests");
        this.guest = "";
        return;
      }
      if (this.guest.trim().length > 0) {
        this.guests.push(
          this.guest[0].toUpperCase() + this.guest.slice(1).toLowerCase()
        );
        this.guestsCapacityPercentage =
          this.guests.length / (this.guestsCapacity / 100);
        this.guest = "";
      }
    }
  }
};
</script>

<style scoped>
form {
  margin-bottom: 2.5rem;
}
input::placeholder {
  font-family: "Noto Serif", serif;
  font-weight: 400;
}
.progress {
  height: 20px;
  border-radius: 10px;
}
.length {
  height: 20px;
  border-radius: 10px;
  background-color: firebrick;
  transition: all 0.6s ease;
}
</style>
