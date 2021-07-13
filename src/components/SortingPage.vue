<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <v-data-table
        :headers="headersForTrainingTable"
        :value="selected"
        :items="trainingData"
        class="elevation-1"
        style="margin-top: 20px"
        :show-select="true"
        item-key="email"
        :hide-default-footer="true"
        no-data-text="Todo didn't create yet..">

<!--      <template v-slot:item.action="{item}">-->
<!--        <div class="action-button-container">-->
<!--          <v-chip outlined-->
<!--                  @click="editTodo(item)"-->
<!--                  color="info">Edit-->
<!--          </v-chip>-->
<!--          <v-chip-->
<!--              outlined-->
<!--              color="success"-->
<!--              style="margin-left: 15px"-->
<!--              @click="doneTodo(item)">Done-->
<!--          </v-chip>-->
<!--        </div>-->
<!--      </template>-->
    </v-data-table>
  </div>
</template>

<script>
export default {
  name: 'SortingPage',
  props: {
    msg: String
  },
  data() {
    return {
      headersForTrainingTable: [
        {
          text: 'Email',
          align: 'left',
          sortable: false,

          value: 'email',
          class: 'table-header-text'
        },
        {text: 'Potatoes', value: 'potatoes', class: 'table-header-text'},
        {text: 'Tags', value: 'tag',  class: 'table-header-text'},
        {text: 'Full name', value: 'fullName', class: 'table-header-text'},
        {text: 'Location', value: 'location',  class: 'table-header-text'},
        {text: 'Date', value: 'date', class: 'table-header-text'}
      ],

      selected:[],
      trainingData: [

      ]
    };
  },

  created() {
    this.trainingData.push(this.generateSimpleData());
    let seconobject = this.generateSimpleData();
    seconobject.index=2
    seconobject.email='tuly@gmail.com'
    this.trainingData.push(seconobject);
  },
  methods:{

   generateSimpleData(){
      let object = {};
      object.index=1;
      object.email = "rocky.ginger@gmail.com"
      object.potatoes = 5;
      object.tag = "Customer";
      object.fullName = "Salahin Rocky";
      object.location = "Bangladesh";
      object.date = "2021-07-13";
      return object;
    }
  }
}
</script>
