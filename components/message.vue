<template>
  <div class="notification rounded border w-full px-3 py-2">
    {{ message }}
  </div>
</template>

<script>
export default {
  name: 'message',
  props: ['message']
}
</script>
