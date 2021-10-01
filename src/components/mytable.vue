<template>
  <b-container no-guters fluid class="you">
    <!-- User Interface controls -->
    <b-row>
      <!--<b-col lg="6" class="my-1">
          <b-form-group
            label="Sort"
            label-for="sort-by-select"
            label-cols-sm="3"
            label-align-sm="right"
            label-size="sm"
            class="mb-0"
            v-slot="{ ariaDescribedby }"
          >
            <b-input-group size="sm">
              <b-form-select
                id="sort-by-select"
                v-model="sortBy"
                :options="sortOptions"
                :aria-describedby="ariaDescribedby"
                class="w-75"
              >
                <template #first>
                  <option value="">-- none --</option>
                </template>
              </b-form-select>
  
              <b-form-select
                v-model="sortDesc"
                :disabled="!sortBy"
                :aria-describedby="ariaDescribedby"
                size="sm"
                class="w-25"
              >
                <option :value="false">Asc</option>
                <option :value="true">Desc</option>
              </b-form-select>  <colgroup><col><  <colgroup><col><col></colgroup>
    <colgroup><col><col><col></colgroup>
    <colgroup><col><col></colgroup>col></colgroup>
    <colgroup><col><col><col></colgroup>
    <colgroup><col><col></colgroup>
            </b-input-group>
          </b-form-group>
        </b-col>-->

      <!--  <b-col lg="6" class="my-1">
          <b-form-group
            label="Initial sort"
            label-for="initial-sort-select"
            label-cols-sm="3"
            label-align-sm="right"
            label-size="sm"
            class="mb-0"
          >
            <b-form-select
              id="initial-sort-select"
              v-model="sortDirection"
              :options="['asc', 'desc', 'last']"
              size="sm"
            ></b-form-select>
          </b-form-group>
        </b-col>-->
      <b-col col-md="1">
        <b-button
          type="button"
          size="sm"
          variant="secondary"
          class="my-1"
          @click="newRecord($event.target)"
        >
          add
        </b-button>

        <br />
      </b-col>

      <b-col lg="6" class="my-1">
        <b-form-group
          label="Filter"
          label-for="filter-input"
          label-cols-sm="3"
          label-align-sm="left"
          label-size="sm"
          class="mb-0"
        >
          <b-input-group size="sm">
            <b-form-input
              id="filter-input"
              v-model="filter"
              type="search"
              placeholder="Type to Search"
            ></b-form-input>

            <b-input-group-append>
              <b-button :disabled="!filter" @click="filter = ''"
                >Clear</b-button
              >
            </b-input-group-append>
          </b-input-group>
        </b-form-group>
      </b-col>

      <!-- <b-col lg="6" class="my-1">
          <b-form-group
            v-model="sortDirection"
            label="Filter On"
            description="Leave all unchecked to filter on all data"
            label-cols-sm="3"
            label-align-sm="right"
            label-size="sm"
            class="mb-0"
            v-slot="{ ariaDescribedby }"
          >
            <b-form-checkbox-group
              v-model="filterOn"
              :aria-describedby="ariaDescribedby"
              class="mt-1"
            >
              <b-form-checkbox value="name">Name</b-form-checkbox>
              <b-form-checkbox value="age">Age</b-form-checkbox>
              <b-form-checkbox value="isActive">Active</b-form-checkbox>
            </b-form-checkbox-group>
          </b-form-group>
        </b-col>-->

      <!-- <b-col sm="5" md="6" class="my-1">
          <b-form-group
            label="Per page"
            label-for="per-page-select"
            label-cols-sm="6"
            label-cols-md="4"
            label-cols-lg="3"
            label-align-sm="right"
            label-size="sm"
            class="mb-0"
          >
            <b-form-select
              id="per-page-select"
              v-model="perPage"
              :options="pageOptions"
              size="sm"
            ></b-form-select>
          </b-form-group>
        </b-col>-->
    </b-row>

    <!-- Main table element -->
    <b-table
      div
      class="too"
      :items="items"
      :fields="fields"
      :current-page="currentPage"
      :per-page="perPage"
      :filter="filter"
      :filter-included-fields="filterOn"
      :sort-by.sync="sortBy"
      :sort-desc.sync="sortDesc"
      :sort-direction="sortDirection"
      small
      responsive
      @filtered="onFiltered"
      head-variant="dark"
    >
      <template #cell(name)="row">
        {{ row.value.first }} {{ row.value.last }}
      </template>

      <template #cell(actions)="row">
        <b-button
          size="sm"
          @click="info(row.item, row.index, $event.target)"
          class="mr-1"
        >
          Info modal
        </b-button>
        <b-button size="sm" @click="row.toggleDetails">
          {{ row.detailsShowing ? "Hide" : "Show" }} Details
        </b-button>
      </template>

      <template #row-details="row">
        <b-card>
          <ul>
            <li v-for="(value, key) in row.item" :key="key">
              {{ key }}: {{ value }}
            </li>
          </ul>
        </b-card>
      </template>
    </b-table>

    <b-modal
      :id="infoModal.id"
      :title="infoModal.title"
      header-class="justify-content-center"
      centered
      hide-footer
      @hide="preventClose"
      ref="carolmodal"
    >
      <template #modal-header>
        <div class="mx-auto">
          <h5>{{ infoModal.title }}</h5>
        </div>
      </template>
      <bobo
        :firstName="infoModal.first"
        :lastName="infoModal.last"
        :age="infoModal.age"
        :adress="infoModal.adress"
        v-on:clear-clicked="hideModal"
        v-on:onsubmit="onFormSubmit"
      >
        <b-button type="submit" div class="btns" variant="primary"
          >submit</b-button
        >

        <b-button type="reset" variant="danger">Reset</b-button>

        <b-button size="sm" variant="danger" @click="cancel()">
          Cancel
        </b-button>
      </bobo>

      <!--<AddTask></AddTask>-->
    </b-modal>

    <b-col sm="7" md="6" class="my-1">
      <b-pagination
        v-model="currentPage"
        :total-rows="totalRows"
        :per-page="perPage"
        align="fill"
        size="sm"
        class="my-0"
      ></b-pagination>
    </b-col>
  </b-container>
</template>
  
  <script>
import bobo from "../components/bobo.vue";
export default {
  components: { bobo },

  data() {
    return {
      items: [
        {
          isActive: true,
          age: 40,
          name: { first: "Dickerson", last: "Macdonald" },
        },
        {
          isActive: true,
          age: 90,
          name: { first: "carol", last: "gathoni" },
          adress: 909087,
        },
        {
          isActive: false,
          age: 60,
          name: { first: "joe", last: "gashero", adress: "4040089" },
          adress: 406878,
        },
        {
          isActive: false,
          age: 21,
          name: { first: "Larsen", last: "Shaw" },
          adress: 77778,
        },

        {
          isActive: false,
          age: 9,
          name: { first: "Mini", last: "Navarro" },
          _rowVariant: "success",
        },
        { isActive: false, age: 89, name: { first: "Geneva", last: "Wilson" } },
        { isActive: true, age: 38, name: { first: "Jami", last: "Carney" } },
        { isActive: false, age: 27, name: { first: "Essie", last: "Dunlap" } },
        { isActive: true, age: 40, name: { first: "Thor", last: "Macdonald" } },
        {
          isActive: true,
          age: 87,
          name: { first: "Larsen", last: "Shaw" },
          _cellVariants: { age: "danger", isActive: "warning" },
        },
        { isActive: false, age: 26, name: { first: "Mitzi", last: "Navarro" } },
        {
          isActive: false,
          age: 22,
          name: { first: "Genevieve", last: "Wilson" },
        },
        { isActive: true, age: 38, name: { first: "John", last: "Carney" } },
        { isActive: false, age: 29, name: { first: "Dick", last: "Dunlap" } },
      ],

      fields: [
        {
          key: "name",
          label: "Person full name",
          sortable: true,
          sortDirection: "desc",
        },
        {
          key: "adress",
          label: "adress",
          sortable: true,
          sortDirection: "desc",
        },
        {
          key: "age",
          label: "Person age",
          sortable: true,
          class: "text-center",
        },
        {
          key: "isActive",
          label: "Is Active",
          formatter: (value) => {
            return value ? "Yes" : "No";
          },
          sortable: true,
          sortByFormatted: true,
          filterByFormatted: true,
        },
        { key: "actions", label: "Actions" },
      ],
      canIClose: false,
      totalRows: 1,
      currentPage: 1,
      perPage: 10,
      pageOptions: [5, 10, 15, { value: 100, text: "Show a lot" }],
      sortBy: "",
      sortDesc: false,
      sortDirection: "asc",
      filter: null,
      filterOn: [],
      infoModal: {
        id: "info-modal",
        title: "",
        content: "",
        first: "",
        last: "",
        age: "",
        adress: "",
      },
    };
  },

  computed: {
    sortOptions() {
      // Create an options list from our fields
      return this.fields
        .filter((f) => f.sortable)
        .map((f) => {
          return { text: f.label, value: f.key };
        });
    },
  },
  mounted() {
    // Set the initial number of items
    this.totalRows = this.items.length;
  },
  methods: {
    onFormSubmit(data) {
      this.items.unshift({
        isActive: true,
        age: data.age,
        adress: data.adress,
        name: { first: data.firstName, last: data.lastName },
      });
      this.totalRows = this.items.length;
      this.canIClose = true;
      this.$refs["carolmodal"].hide();
      this.canIClose = false;
      //console.log("firstName =" + data.firstName);
    },
    hideModal(event) {
      this.canIClose = true;
      this.$refs["carolmodal"].hide();
      console.log(
        "==========================================" + event.lastName
      );
      this.canIClose = false;
    },
    info(item, index, button) {
      this.infoModal.title = item.name.first + " " + item.name.last;

      this.infoModal.first = item.name.first;
      this.infoModal.last = item.name.last;
      this.infoModal.age = item.age;
      this.infoModal.adress = item.adress;
      //

      this.$root.$emit("bv::show::modal", this.infoModal.id, button);
    },

    newRecord() {
      this.infoModal.first = "";
      this.infoModal.last = "";
      this.infoModal.age = "";
      this.infoModal.adress = "";
      this.$root.$emit("bv::show::modal", this.infoModal.id, "button");
    },
    preventClose(event) {
      if (!this.canIClose) {
        event.preventDefault();
      } else {
        this.infoModal.title = "";
        this.infoModal.content = "";
      }
    },

    onFiltered(filteredItems) {
      // Trigger pagination to update the number of buttons/pages due to filtering
      this.totalRows = filteredItems.length;
      this.currentPage = 1;
    },
  },
};
</script>







