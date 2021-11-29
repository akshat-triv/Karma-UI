<template>
  <div class="inputTextWrapper">
    <input
      :id="componentId"
      :type="componentType"
      :name="componentName"
      class="inputTextField"
      :placeholder="componentPlaceholder"
      :value="value"
      :required="required"
      @input="$emit('input', $event.target.value)"
    />
    <label :for="componentId" class="inputTextLabel">{{
      componentPlaceholder
    }}</label>
  </div>
</template>

<script>
export default {
  name: 'InputText',
  props: {
    componentId: {
      type: String,
      required: true,
    },
    componentName: {
      type: String,
      required: true,
    },
    componentPlaceholder: {
      type: String,
      required: true,
    },
    componentType: {
      type: String,
      default: 'text',
    },
    value: {
      type: String,
      default: '',
    },
    required: {
      type: Boolean,
      default: true,
    },
  },
}
</script>

<style lang="scss" scoped>
.inputTextField {
  border: none;
  outline: none;
  padding: 1rem;
  width: 100%;
  height: 100%;
  font-size: 1.6rem;
  background: transparent;
  position: relative;
  z-index: 2;

  &::placeholder {
    color: var(--text2);
  }
}

.inputTextWrapper {
  background: var(--surface2);
  width: 30rem;
  border-radius: 6px;
  position: relative;

  &:not(:last-of-type) {
    margin-bottom: 3rem;
  }
}

.inputTextLabel {
  position: absolute;
  z-index: 1;
  left: 0;
  top: 50%;
  opacity: 1;
  transform: translate(1rem, 110%);
  transition: transform 0.3s, opacity 0.2s ease-in;
  color: var(--text2);
  font-size: 1.4rem;
  font-weight: 600;
}

.inputTextField:placeholder-shown + .inputTextLabel {
  transform: translate(1rem, -50%);
  opacity: 0;
}
</style>
