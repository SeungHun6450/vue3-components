<!-- 컴포넌트 Provide / Inject -->
<template>
  <div>
    Child: {{ msg.value }}
  </div>
</template>

<script>
export default {
  // provide사용 시 inject를 사용
  // props: {
  //   msg: {
  //     type: String,
  //     default: ''
  //   }
  // }
  inject :['msg']
}
</script>