<template>
  <div class="content">
    <div class="md-layout">
      <div
        class="md-layout-item md-medium-size-100 md-xsmall-size-100 md-size-100"
      >
        <md-card v-for="(view, index) in views" :key="index">
          <md-card-header data-background-color="green">
            <h4 class="title">Simple Table</h4>
            <p class="category">Here is a subtitle for this table</p>
          </md-card-header>
          <md-card-content>
            <simple-table table-header-color="green"></simple-table>
          </md-card-content>
        </md-card>
      </div>

      <!-- <div
        class="md-layout-item md-medium-size-100 md-xsmall-size-100 md-size-100"
      >
        <md-card class="md-card-plain">
          <md-card-header data-background-color="green">
            <h4 class="title">Table on Plain Background</h4>
            <p class="category">Here is a subtitle for this table</p>
          </md-card-header>
          <md-card-content>
            <ordered-table></ordered-table>
          </md-card-content>
        </md-card>
      </div> -->
    </div>
  </div>
</template>

<script>
import { SimpleTable, OrderedTable } from "@/components";
import axios from 'axios';

export default {
  components: {
    // OrderedTable,
    SimpleTable
  },
  props: {
    user_id: String
  },
  data() {
    return {
      views: []
    }
  },
  mounted() {
    let params = {user_id: this.user_id}
    axios.get("http://localhost:5000/views", { params })
    .then(response => this.views=response.data)
  }
};
</script>
