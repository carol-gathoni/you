
<template>
  <div class="form1">
    <b-form inline="onSubmit">
      <b-form-group id="input-group-2" label="full name " label-for="input-2">
        <!-- <h1>{{ index.firstName }}</h1>-->

        <b-form-input
          id="input-2"
          type="text"
          placeholder=""
          required
        ></b-form-input>
      </b-form-group>
      <b-form-group id="input-group-2" label="email" label-for="input-2">
        <!--  <h1>{{ index.lastName  }}</h1>-->

        <b-form-input
          id="input-2"
          type="text"
          placeholder=""
          required
        ></b-form-input>
      </b-form-group>
      <b-form-group id="input-group-1" label="person age " label-for="input-1">
        <!--<h1>{{ index.age  }}</h1>-->
        <b-form-input
          id="input-1"
          type="number"
          placeholder=""
          required
        ></b-form-input>
      </b-form-group>
      <b-form-group id="input-group-2" label="adress  nb " label-for="input-2">
        <!-- <h1>{{ index.firstName }}</h1>-->

        <b-form-input
          id="input-2"
          type="text"
          placeholder=""
          required
        ></b-form-input>
      </b-form-group>
    </b-form>
    <bobo></bobo>
  </div>
</template>





<style scoped>
.form1 {
  width: 50%;
  background-color: whitesmoke;
}
#input-1 {
  margin-left: 10px;
  margin-bottom: 15px;
  width: 188%;
}
#input-2 {
  margin-left: 10px;
  margin-bottom: 15px;
  width: 188%;
}
#input-group-2 {
}
.bbb {
  margin-right: 3px;
}
</style>

