<!-- 컴포넌트 Provide / Inject -->
<template>
  <!-- <Child :msg="msg" /> -->
  <Child />
</template>

<script>
import Child from '~/components/Child'

export default {
  components: {
    Child
  }  
  // provide 사용 시 필요 없어짐
  // ,
  // props: {
  //   msg: {
  //     type: String,
  //     default: ''
  //   }
  // }
}
</script>