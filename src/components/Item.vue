<template>
  <div :class="classObject">
    <input
      type="checkbox"
      :checked="completed"
      @change="toggle"
    >
    {{ title }}
    <button @click.prevent="remove">
      [x]
    </button>
  </div>
</template>

<script>
import eventHub from '../event-hub'

export default {
  name: 'item',
  props: {
    id: {
      type: Number,
      required: true
    },
    completed: {
      type: Boolean,
      required: true
    },
    title: {
      type: String,
      required: true
    }
  },
  computed: {
    classObject: function () {
      return {
        item: true,
        isCompleted: this.completed
      }
    }
  },
  methods: {
    remove: function () {
      eventHub.$emit('remove', this.id)
    },
    toggle: function () {
      eventHub.$emit('toggle', this.id)
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.item.isCompleted {
  text-decoration: line-through;
}
</style>
