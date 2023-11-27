<template>
  <div class="h-20 w-20 mr-6 relative">
    <div class="absolute inset-0 flex items-center justify-center">
      <span class="text-blue-500 text-sm font-medium leading-tight">
        {{ progress }}%
      </span>
    </div>
    <svg class="-rotate-90" viewBox="0 0 120 120">
      <circle
        cx="60"
        cy="60"
        :r="radius"
        fill="none"
        stroke-width="12"
        class="stroke-current text-gray-200"
      />

      <circle
        cx="60"
        cy="60"
        :r="radius"
        fill="none"
        stroke-width="12"
        class="stroke-current text-blue-500"
        :stroke-dasharray="dash"
        :stroke-dashoffset="offset"
      />
    </svg>
  </div>
</template>

<script>
  export default {
    props: {
      progress: {
        required: true,
        type: Number
      }
    },

    data () {
      return {
        radius: 54
      }
    },

    computed: {
      dash () {
        return 2 * Math.PI * this.radius
      },

      offset () {
        let circ = this.dash
        let progress = this.progress / 100

        return circ * (1 - progress)
      }
    }
  }
</script>