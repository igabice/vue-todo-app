<template>
    <div class='ui centered card'>
        <div class="content">
                <div class="header">
                    {{ todo.title}}
                </div>
                <div class="meta">
                    {{ todo.project}}
                </div>
                <div class="extra content">
                    <span class='right floated edit icon' v-on:click="showForm">
                        <i class="edit icon"></i>
                    </span>
                    <span class='right floated edit icon' v-on:click="deleteTodo(todo)">
                        <i class="trash icon"></i>
                    </span>
                    <span class='right floated edit icon' v-on:click="completeTodo(todo)">
                        <i class="play icon"></i>
                    </span>
                </div>
            </div>
            <div class='content' v-show="isEditing">
                <div class="ui form">
                    <div class="field">
                        <label>Title</label>
                        <input type='text' v-model='todo.title'>
                    </div>
                    <div class="field">
                        <label>Project</label>
                        <input type='text' v-model='todo.project'>
                    </div>
                    <div class="ui two button attached buttons">
                        <button class="ui basic blue button" v-on:click="hideForm">
                        Close X 
                        </button>
                    </div>
                </div>
            </div>
            <div class='ui bottom attached green basic butoon' v-show="todo.done">
            Completed
            </div>
            <div class='ui bottom attached red basic butoon' v-show="!todo.done">
                Complete
            </div>  
    </div>
</template>

<script type='text/javascript'>
export default {
    props: ['todo'],
    data() {
        return {
            isEditing: false,
            
        }
    },
    methods: {
        showForm() {
            this.isEditing = true;
        },
        hideForm() {
            this.isEditing = false;
        },
        deleteTodo(todo) {
            this.$emit('delete-todo', todo);
        },
        completeTodo(todo){
            this.$emit('complete-todo', todo);
        },
    },
}
</script>