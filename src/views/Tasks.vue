
<template>
  <div class="home">
    <v-alert type="warning" dense v-if="type">test </v-alert>
     <v-text-field
     v-model="newTaskTitle"
     @click:append="addTask"
     @keyup.enter="addTask"
     class="pa-3"
     label="Add Task"
     append-icon="mdi-plus"
     hide-details
     clearable
          >
          </v-text-field>
    <v-list
    class="pt-0"
      flat>
      <div v-for="task in tasks"
        :key='tasks.id'>
        <v-list-item 
        @click="doneTask(task.id)"
        :class="{'blue lighten-5': task.done}"
        >
          <template v-slot:default>
            <v-list-item-action>
              <v-checkbox
                :input-value="task.done"
                color="primary"
              ></v-checkbox>
            </v-list-item-action>

            <v-list-item-content>
              <v-list-item-title>{{task.title}}</v-list-item-title>
              
            </v-list-item-content>
            <v-list-item-action>
          <v-btn 
          @click.stop="deleteTask(task.id)"
          icon>
            <v-icon color="primary lighten-1">mdi-delete</v-icon>
          </v-btn>
        </v-list-item-action>
          </template>
        </v-list-item>
        <v-divider> </v-divider>
       </div>

       
        
    </v-list>
  </div>
</template>

<script>
// @ is an alias to /src


export default {
  name: 'Tasks',
  data () {
    return {
      newTaskTitle: '',
      tasks: [
      ],
      type: null
    }
  },
  methods: {
    taskAlert(type) {if (this.newTaskTitle.length === 0) {
      console.log("test")
    }},
    addTask() {
      /* if (this.newTaskTitle.length === 0){
        return (alert("Enter at least 1 character!"))
      } */
      
      let newTask = {
        id: Date.now(),
        title: this.newTaskTitle,
        done: false
      }
      
      this.tasks.push(newTask)
      this.newTaskTitle = ''
      
      
    },
    doneTask(id) {
      let task = this.tasks.filter(task => task.id === id)[0]
      task.done = !task.done
    },
    deleteTask(id) {
      this.tasks = this.tasks.filter(task => task.id !== id)
    },
    

  }
}
</script>
