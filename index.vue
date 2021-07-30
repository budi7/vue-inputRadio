<template>
  <div class="row align-items-center mb-4">
    <div
      v-for="(dt,i) in options"
      :key="'input-' + i"
      :class="`col-auto px-0 ${inputClass}`"
    >
      <div class="form-check form-check-inline border mb-0 form-check-border py-1">
        <input
          :id="`radio-${name}-${i}`"
          :disabled="disabled"
          class="form-check-input"
          type="radio"
          :name="name"
          :checked="(input && (input === i.toString()))"
          @click="handleClick(i.toString())"
        >
        <label class="form-check-label" :for="`radio-${name}-${i}`">
          {{ dt[lang] ? dt[lang] : dt }}
        </label>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    value: {
      type: [String, Number],
      default: null
    },
    options: {
      default () { return [] },
      type: [Object, Array]
    },
    name: {
      type: String,
      default: 'input'
    },
    disabled: {
      type: Boolean,
      default: false
    },
    inputClass: {
      type: String,
      default: ''
    }
  },
  data () {
    return {
      lang: this.$store.getters['app/getLanguage'],
      input: null
    }
  },
  watch: {
    input (newVal) {
      this.$emit('changed', newVal)
    }
  },
  mounted () {
    this.input = this.value || this.value === 0 ? this.value.toString() : null
  },
  methods: {
    handleClick (i) {
      this.input = i
      this.$emit('input', i.toString())
    }
  }
}
</script>
