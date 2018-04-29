<template>
  <div>
      {{ detail }} {{ $route.params.name }}
  </div>
</template>

<script>
export default {
  props: ['detail']
}
</script>
