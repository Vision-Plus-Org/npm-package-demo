<template>
  <button
    class="v-button"
    :class="[
      `is-${color}`,
      `v-button--${size}`,
      {
        'v-button--plain': plain
      }
    ]"
  >
    <slot></slot>
  </button>
</template>

<script setup lang="ts">
const enum COLOR {
  orange,
  'marker-red'
}

const enum SIZE {
  small,
  medium
}

interface Props {
  color?: keyof typeof COLOR;
  size?: keyof typeof SIZE;
  plain?: boolean
}
defineProps<Props>()
</script>

<style lang="scss">
$font-size-xs: 12px;
$font-size-sm: 14px;
$font-size-base: 16px;
$font-size-lg: 18px;
$font-size-xl: 20px;
$font-size-2xl: 22px;
$font-size-3xl: 24px;

$wl-primary-600: #417478;
$wl-primary-700: #286157;
$wl-orange: #c5640c;
$wl-marker-red: #a25a5a;

$wl-gray-100: #f7f7f6; // Page Background
$wl-gray-200: #e9ecec; // Tab1 Background, Table Header Background
$wl-gray-300: #f5f5f5; // Hover (Gray), Chart Background, Popup Header Background
$wl-gray-500: #dde0dc; // Divide Line, 按鈕 Disabled Background,
$wl-gray-700: #a4a4a4; // 按鈕 disable 文字, 元件 disable, text input suffix
$wl-gray-750: #727677; // text input placeholder
$wl-gray-800: #5d676a; // 次要文字, Input Box border
$wl-gray-900: #242f31; // 主要文字

$btn-border-radius:  4px;
$btn-border-small-radius:  4px;
$btn-border-medium-radius:  6px;
$btn-border-round-radius:  20px;

.v-button {
  display: inline-flex;
  justify-content: center;
  align-items: center;
  position: relative;
  white-space: nowrap;
  cursor: pointer;
  -webkit-appearance: none;
  outline: none;
  margin: 0;
  transition: all .15s;
  font-weight: 400;
  user-select: none;
  padding: 4px 12px;
  font-size: $font-size-base;
  line-height: $font-size-3xl;
  color: #fff;
  background-color: $wl-primary-700;
  border: none;
  border-radius: $btn-border-radius;
  border-color: transparent;
  vertical-align: middle;

  $this: &;

  &::before {
    content: '';
    box-sizing: inherit;
    display: block;
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    border: 1px solid transparent;
    border-color: inherit;
    border-radius: inherit;
    transition: inherit;
  }

  &:hover {
    background-color: $wl-primary-600;
  }

  &:active {
    background-color: $wl-primary-700;
    outline: none;
  }

  &::-moz-focus-inner {
    border: 0;
  }

  & + & {
    margin-left: 8px;
  }

  &.is-disabled {
    &,
    &:hover,
    &:active {
      cursor: not-allowed;
      color: $wl-gray-700;
      background-color: $wl-gray-500;
      border-color: $wl-gray-500;
    }
  }

  &--plain {
    background-color: transparent;
    border-color: $wl-primary-700;
    color: $wl-primary-700;

    &:hover {
      background-color: $wl-primary-600;
      border-color: $wl-primary-600;
      color: #fff;
    }

    &:active {
      background-color: $wl-primary-700;
      border-color: $wl-primary-700;
      color: #fff;
    }

    &.is-orange {
      background-color: transparent;
      border-color: $wl-orange;
      color: $wl-orange;

      &:hover,
      &:active {
        background-color: $wl-orange;
        border-color: $wl-orange;
        color: #fff;
      }
    }

    &.is-marker-red {
      background-color: transparent;
      border-color: $wl-marker-red;
      color: $wl-marker-red;

      &:hover,
      &:active {
        background-color: $wl-marker-red;
        border-color: $wl-marker-red;
        color: #fff;
      }
    }

    &.is-disabled {
      &,
      &:hover,
      &:active {
        color: $wl-gray-700;
        background-color: transparent;
        border-color: $wl-gray-700;
      }
    }
  }

  // setup button size
  &--medium {
    padding: 8px 16px;
    font-size: $font-size-base;
    line-height: $font-size-3xl;
    border-radius: $btn-border-medium-radius;

    &.is-with-icon {
      padding: 4px 12px 4px 8px;
      line-height: 32px;
    }
  }

  &--small {
    padding: 4px 12px;
    font-size: $font-size-sm;
    line-height: $font-size-base;
    border-radius: $btn-border-small-radius;

    &.is-with-icon {
      padding: 4px 12px 4px 8px;
      line-height: $font-size-base;
    }
  }

  &--round {
    border-radius: $btn-border-round-radius;
  }

  &.is-orange {
    background-color: $wl-orange;
  }

  &.is-marker-red {
    background-color: $wl-marker-red;
  }
}
</style>
