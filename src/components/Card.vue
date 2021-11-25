<template>
  <div class="card" @click="selectCard">
    <div v-if="visible" class="card-face is-front">
      {{value}}
    </div>
    <div v-else class="card-face is-back">
      back
    </div>
  </div>
</template>

<script>
export default {
  name: "Card",
  props: {
    position: {
      type: Number,
      required: true
    },
    value: {
      type: Number,
      required: true
    },
    visible: {
      type: Boolean,
      default: false
    }
  },
  setup (props, context) {
    const selectCard = () => {
      context.emit('select-card', {
        position: props.position
      })
    }

    return {
      selectCard
    }
  }

}
</script>

<style scoped>
.card {
  border: 5px solid #ccc;
  position: relative;
}
.card-face {
  height:100%;
  width:100%;
  position: absolute;
}

.card-face.is-front {
  background-color: red;
  color:white
}

.card-face.is-back {
  background-color: blue;
}
</style>
