<template>
  <li class="tasks-item">
    <input type="checkbox" @change="$emit('complete')" :checked="task.completed" :id="'task-' + task.id" name="check" />
    <label :for="'task-' + task.id">{{task.title}}</label>
  </li>
</template>

<script>
export default {
  name: 'TaskItem',
  props: {
    task: Object
  }
}
</script>

<style scoped lang="scss">
  label {
    position: relative;
    margin-left: 35px;
    cursor: pointer;
    color: #fff;
    font-weight: 500;
    font-size: 16px;
  }
  input[type=checkbox] {
    display: none;
  }
  input[type=checkbox] + label:before {
    position: absolute;
    content: "";
    left: -35px;
    top: calc(50% - 10px);
    display: inline-block;
    border-radius: 6px;
    font-size: 20px;
    line-height: 22px;
    background: #4F5565;
    height: 20px;
    width: 20px;
    text-align: center;
    vertical-align: middle;
    transition: color ease .3s;
    margin-right: 15px;
    cursor: pointer;
  }
  input[type=checkbox]:checked + label:before{
    background: #FF8469;
  }
  input[type=checkbox]:checked + label:after {
    position: absolute;
    content: '';
    top: calc(50% - 8px);
    left: -29px;
    width: 6px;
    height: 10px;
    transform: rotate(40deg);
    border-right: 2px solid #fff;
    border-bottom: 2px solid #fff;
    color: #fff;
    font-weight: 500;
    font-size: 16px;
    line-height: 20px;
  }
  input[type=checkbox]:checked + label {
    text-decoration: line-through;
  }
</style>
