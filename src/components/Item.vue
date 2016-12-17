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
      this.$emit('remove', this.id)
    },
    toggle: function () {
      this.$emit('toggle', this.id)
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
