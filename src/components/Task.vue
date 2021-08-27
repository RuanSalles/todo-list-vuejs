<template>
  <div 
  @click="$emit('taskStateChanged', task)"
  class="task" 
  :class="stateClass">
      <span @click.stop="$emit('taskDeleted')" class="close">x</span>
      <p>{{ task.name }}</p>
  </div>
</template>

<script>
export default {
    props: {
        task: { type: Object, required: true}
    },
    computed: {
        stateClass() {
            return {
                pending: this.task.pending,
                done: !this.task.pending
            }
        }
    }
}
</script>

<style>
.task {
    box-sizing: border-box;
    width: 250px;
    height: 100px;
    padding: 10px;
    border-radius: 5px;
    font-size: 1.5rem;
    font-weight: 300;
    cursor: pointer;
    user-select: none;
    display: flex;
    justify-content: center;
    align-items: center;
    position: relative;
}

.pending {
    border-left: 12px solid tomato;
    background-color: red;
}

.done {
    color: silver;
    border-left: 12px solid yellowgreen;
    background-color: green;
    text-decoration: line-through;
}

.pending .close {
    background-color: maroon;
}

.done .close {
    background-color: rgb(20, 75, 4);
}

.close {
    position: absolute;
    right: 10px;
    top: 10px;
    font-size: 0.9rem;
    font-weight: 600;
    height: 20px;
    width: 20px;
    border-radius: 10px;
    display: flex;
    justify-content: center;
}
</style>