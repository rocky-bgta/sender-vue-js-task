<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <v-data-table
        :headers="headersForTrainingTable"
        :value="selected"
        :items="trainingData"
        class="elevation-1"
        :hide-default-header="false"
        style="margin-top: 20px"
        :show-select="true"
        item-key="email"
        :hide-default-footer="true"
        no-data-text="Todo didn't create yet..">


      <template v-slot:body="props">
        <draggable :list="props.items" tag="tbody"
                   @drop='onDrop($event, 1)'
                   @change="onDragOver"
                   @start="onDragStart"
                   @end="onDragEnd"

        >
          <tr v-for="(trainingData, index) in props.items" :key="index">
            <td>

                <v-checkbox></v-checkbox>

            </td>
            <td> {{ trainingData.email }} </td>
            <td> {{ trainingData.potatoes }} </td>
            <td> {{ trainingData.tag }} </td>
            <td> {{ trainingData.fullName }} </td>
            <td> {{ trainingData.location }} </td>
            <td> {{ trainingData.date }} </td>
          </tr>
        </draggable>
      </template>

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
import Draggable from 'vuedraggable';
export default {
  name: 'SortingPage',
  props: {
    msg: String
  },
  components:{
    Draggable
  },
  data() {
    return {
      headersForTrainingTable: [
        {
          text: 'Email',
          align: 'left',
          sortable: false,

          value: 'email',

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
    seconobject.index=2;
    seconobject.email='tuly@gmail.com';
    seconobject.potatoes=10;
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
    },

    onDragOver(){
      console.log('On drag over event')
    },

    onDragStart(){
     console.log('On drag start event')
    },

    onDragEnd(){
      console.log('On drag end event')
    },


    onDrop(event, take){
     console.log("Event drop"+ event + "taken: "+take);
    }
  }
}
</script>

<style lang="scss">
.page--table {
  .page {
    &__table {
      margin-top: 20px;
    }
    &__grab-icon {
      cursor: move;
    }
  }
}
</style>
