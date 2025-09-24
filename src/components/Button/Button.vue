<template>
    <button
      :class="[
        'v-btn',
        `v-btn--${type}`,
        `v-btn--${size}`,
        {
          'v-btn--disabled': disabled,
          'v-btn--block': block
        }
      ]"
      :disabled="disabled"
      @click="handleClick"
    >
      <slot></slot>
    </button>
  </template>
  
  <script>
  export default {
    name: 'VButton',
    props: {
      type: {
        type: String,
        default: 'primary',
        validator: (value) => ['primary', 'secondary', 'danger'].includes(value)
      },
      size: {
        type: String,
        default: 'medium',
        validator: (value) => ['small', 'medium', 'large'].includes(value)
      },
      disabled: {
        type: Boolean,
        default: false
      },
      block: {
        type: Boolean,
        default: false
      }
    },
    methods: {
      handleClick(event) {
        this.$emit('click', event)
      }
    }
  }
  </script>
  
  <style lang="scss" scoped>
  @import '../../styles/variables';
  
  .v-btn {
    display: inline-flex;
    align-items: center;
    justify-content: center;
    border: none;
    border-radius: 4px;
    cursor: pointer;
    font-family: inherit;
    font-weight: 500;
    transition: all 0.3s ease;
  
    &--primary {
      background-color: $primary-color;
      color: white;
  
      &:hover {
        background-color: darken($primary-color, 10%);
      }
    }
  
    &--secondary {
      background-color: $secondary-color;
      color: white;
  
      &:hover {
        background-color: darken($secondary-color, 10%);
      }
    }
  
    &--danger {
      background-color: $danger-color;
      color: white;
  
      &:hover {
        background-color: darken($danger-color, 10%);
      }
    }
  
    &--small {
      padding: 4px 8px;
      font-size: 12px;
    }
  
    &--medium {
      padding: 8px 16px;
      font-size: 14px;
    }
  
    &--large {
      padding: 12px 24px;
      font-size: 16px;
    }
  
    &--disabled {
      opacity: 0.6;
      cursor: not-allowed;
    }
  
    &--block {
      display: block;
      width: 100%;
    }
  }
  </style>