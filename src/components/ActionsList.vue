<template>
  <div
    class="beer-card-actions"
  >
    <template
      v-for="(action, index) in actions"
    >
      <div
        :key="index" 
        class="beer-card-action"
        @click="$emit('action-click', action.name)"
      >
        <span :title="action.label">
          {{ action.emoji }}
        </span>
      </div>
    </template>
  </div>
</template>

<script>
export default {
  name: 'ActionsList',
  props:{
    actions: {
      default: () => [],
      type: Array
    }
  }
}
</script>

<style scoped>
.beer-card-actions{
  margin-left: auto;
  display: flex;
  flex-direction: column;
  flex: 0 0 auto;
}

.beer-card-action{
  cursor: pointer;
  margin: 4px 0;
  user-select:none;
  text-align: right;
}
</style>