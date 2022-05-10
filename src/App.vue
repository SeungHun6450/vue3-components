<!-- 컴포넌트 기초 -->
<!-- props 사용: 부모-자식간의 데이터 통신이라 한다. 부모 컴포넌트에서 자식 컴포넌트로 특정 데이터를 전달하는 용도로 사용하기 때문이다. -->
<!-- 해당 컴포넌트에 html속성처럼 붙어있을때, 내용에 값이 연결되어 있을 때 컴포넌트 내부에서 어떻게 처리 할지를 정의하는 개념으로 props옵션을 사용한다. -->
<!-- <template>
  <MyBtn>Banana</MyBtn>
  <MyBtn 
    :color="color">
    <span style="color:red;">Banana</span>  
  </MyBtn>
  <MyBtn 
    large
    color="royalblue">
    Apple  
  </MyBtn>
  <MyBtn>Cherry</MyBtn>
</template>

<script>
import MyBtn from '~/components/MyBtn'

export default {
  components: {
    MyBtn
  },
  data() {
    return {
      color: '#000'
    }
  }
}
</script> -->

<!-- 컴포넌트 속성, 상속 -->
<!-- <template>
  <MyBtn 
    class="Hun"
    style="color: red;"
    title="Hello world!">
    Banana
  </MyBtn>
</template>

<script>
import MyBtn from '~/components/MyBtn'

export default {
  components: {
    MyBtn
  }
}
</script> -->

<!-- 컴포넌트 emit -->
<!-- <template>
  <MyBtn @click="log" @change-msg="logMsg">
    Banana
  </MyBtn>
</template>

<script>
import MyBtn from '~/components/MyBtn'

export default {
  components: {
    MyBtn
  },
  methods: {
    log(event) {
      console.log('Click!')
      console.log(event)
    },
    logMsg(msg) {
      console.log(msg)
    } 
  }
}
</script> -->


<!-- 컴포넌트 v-slot: (약어: #) -->
<!-- <template>
  <MyBtn>
    <template #text>
      <span>Banana</span>
    </template>
    <template #icon>
      <span>(B)</span>
    </template>
  </MyBtn>
</template>

<script>
import MyBtn from '~/components/MyBtn'

export default {
  components: {
    MyBtn
  }
}
</script> -->


<!-- 컴포넌트 Provide / Inject -->
<!-- Child 기준 조상 컴포넌트, 자식 컴포넌트로 데이터를 내려줄때 props를 사용한다.
     props는 바로 아래의 자식 컴포넌트에게만 적용이 되기 때문에 이 과정을 생략하기 위해
     provide와 inject를 사용한다. 단 반응성을 가지지 않는다는 단점을 가지게 된다.
     그래서 computed()를 사용하여 반응성을 가지게 만든 것이다. -->
<!-- <template>
  <button @click="message = 'Good?'">
    Click!
  </button>
  <h1>App: {{ message }}</h1> -->
  <!-- <Parent :msg="message" /> -->
  <!-- <Parent />
</template>

<script>
import Parent from '~/components/Parent'
import { computed } from 'vue'

export default {
  components: {
    Parent
  },
  data() {
    return {
      message: 'Hello world!'
    }
  },
  provide() {
    // 반응성을 유지해주는 데이터를 만들기 위해 computed() 사용
    return {
      msg: computed(() => this.message)
    }
  }
}
</script> -->

<!-- 컴포넌트 Refs(reference: 참조): 해당하는 요소를 참조한다.
해당 요소들은 html과 연결된 직후에만 사용할 수 있다. 즉, created()에는 사용할 수 없고
mounted()에는 사용할 수 있다.
컴포넌트에서 ref를 통해 참조할 경우 참조된 이름의 뒤쪽에 $el을 사용해야 참조할 수 있다.
최상위 요소가 여러개이면 객체 데이터로 추출된다.
최상위 요소가 여러개인 곳에서 원하는 부분을 참조하려면 원하는 최상위 요소에 ref를 작성하여 참조를 해주면 된다.
 -->
<template>
  <!-- 1. -->
  <!-- <h1 id="hello"> -->
  <!-- 2. ref사용  -->
  <!-- <h1 ref="hello">
    Hello world!
  </h1> -->
  <!-- 3. import해서 사용 -->
  <Hello ref="hello" />
</template>

<script>
import Hello from '~/components/Refs'

export default {
  components: {
    Hello
  },
  mounted() {
    // 1.
    // const h1El = document.querySelector('#hello')
    // console.log(h1El.textContent)
    
    // 2. ref사용
    // this.$refs.hello
    // console.log(this.$refs.hello.textContent)
    
    // 3. import 해서 사용
    console.log(this.$refs.$el) // <h1>Hello~</h1>

    // 4. 최상위 요소가 여러개인 경우
    console.log(this.$refs.hello.$refs.good)
  }
}
</script>