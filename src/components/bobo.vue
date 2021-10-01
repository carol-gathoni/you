
<template>
  <div class="karrot">
    <b-form inline @submit="onSubmit" v-if="show">
      <b-form-group id="input-group-2" label="first name " label-for="input-2">
        <!-- <h1>{{ index.firstName }}</h1>-->

        <b-form-input
          id="input-2"
          :value="form.firstName"
          type="text"
          v-model="form.firstName"
          placeholder=""
          required
        ></b-form-input>
      </b-form-group>
      <b-form-group id="input-group-2" label="last name " label-for="input-2">
        <!--  <h1>{{ index.lastName  }}</h1>-->

        <b-form-input
          id="input-2"
          type="text"
          v-model="form.lastName"
          :value="form.lastName"
          placeholder=""
          required
        ></b-form-input>
      </b-form-group>
      <b-form-group id="input-group-1" label="person age " label-for="input-1">
        <!--<h1>{{ index.age  }}</h1>-->
        <b-form-input
          id="input-1"
          :value="form.age"
          v-model="form.age"
          type="number"
          placeholder=""
          required
        ></b-form-input>
      </b-form-group>
      <b-form-group id="input-group-2" label="adress  nb " label-for="input-2">
        <!-- <h1>{{ index.firstName }}</h1>-->

        <b-form-input
          id="input-2"
          :value="form.adress"
          type="text"
          v-model="form.adress"
          placeholder=""
          required
        ></b-form-input>
      </b-form-group>
      <b-form-group id="input-group-3">
        <b-button class="bbb" size="sm" type="submit" variant="primary"
          >Submit</b-button
        >
        <b-button size="sm" type="reset" @click="onReset" variant="warn"
          >Reset</b-button
        >
        <b-button size="sm" v-on:click="hideinfoModal" variant="danger"
          >cancel</b-button
        >
      </b-form-group>
    </b-form>

    <!-- <b-card class="mt-3" header="Form Data Result">
      <pre class="m-0">{{ form }}</pre>
    </b-card>-->
  </div>
</template>

<script>
export default {
  data() {
    return {
      form: {
        age: "",
        lastName: "",
        firstName: "",
        adress: "",
      },

      show: true,
    };
  },
  props: ["firstName", "lastName", "age", "adress"],
  mounted() {
    this.updateFormField();
  },

  methods: {
    hideinfoModal() {
      console.log("-------------------------------------------");
      this.$emit("clear-clicked", this.form);
    },

    updateFormField() {
      this.form.age = this.age;
      this.form.firstName = this.firstName;
      this.form.lastName = this.lastName;
      this.form.adress = this.adress;
    },

    onSubmit(event) {
      event.preventDefault();
      this.$emit("onsubmit", this.form);
    },

    onReset(event) {
      event.preventDefault();
      // Reset our form values
      this.form.age = "";
      event.preventDefault();
      // Reset our form values
      this.form.lastName = "";
      event.preventDefault();
      // Reset our form values
      this.form.firstName = "";
      event.preventDefault();
      // Reset our form values
      this.form.adress = "";
      // Trick to reset/clear native browser form validation state
      this.show = false;
      this.$nextTick(() => {
        this.show = true;
      });
    },
  },
};
</script>


<style scoped>
.karrot {
  width: 100%;
  background-color: whitesmoke;
}
#input-1 {
  margin-left: 10px;
  margin-bottom: 15px;
  width: 165%;
}
#input-2 {
  margin-left: 10px;
  margin-bottom: 15px;
  width: 168%;
}
#input-group-2 {
}
.bbb {
  margin-right: 3px;
}
</style>















 