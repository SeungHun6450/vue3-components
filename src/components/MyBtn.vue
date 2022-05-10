<!-- 컴포넌트 기초 -->
<!-- <template>
  <div 
    :class="{ large }"
    :style="{ backgroundColor: color }"
    class="btn">
    <slot></slot>
  </div>
</template>

<script>
export default {
  // props: 컴포넌트가 실행될 때 속성처럼 받아내는 내용들을 받아줄 수 있는 옵션이다.
  // 해당 컴포넌트에 html속성처럼 붙어있을때, 내용에 값이 연결되어 있을 때 컴포넌트 내부에서 어떻게 처리 할지를 정의하는 개념으로 props옵션을 사용한다.
  props: {
    color: {
      type: String,
      default: 'gray'
    },
    large: {
      type: Boolean,
      default: false
    },
    text: {
      type: String,
      default: ''
    }
  }
}
</script>

<style scoped lang="scss">
.btn {
  display: inline-block;
  margin: 4px;
  padding: 6px 12px;
  border-radius: 4px;
  background-color: gray;
  color: white;
  cursor: pointer;
    &.large {
    font-size: 20px;
    padding: 10px 20px;
  }
}
</style> -->

<!-- 컴포넌트 속성, 상속 -->
<!-- template의 바로 아래 자식요소를 최상위(루트)요소라고 부른다 -->
<!-- 최상위 요소가 2개 이상인 경우 부모 컴포넌트에서 제대로 적용이 되지 않는다. -->
<!-- <template>
  <div class="btn">
    <slot></slot>
  </div>
  <h1 v-bind="$attrs"></h1>
  <h1 
    :class="$attrs.class"
    :style="$attrs.style"></h1>
</template>

<script>
export default {
  // 최상위 요소가 하나만 있을 때에도 상속하지 않겠다고 선언
  // 이후 원하는 요소를 연결을 해주고 싶다면 위에 $attrs을 사용한다.
  inheritAttrs: false,
  created() {
    console.log(this.$attrs)
  }
}
</script>

<style scoped>
.btn {
  display: inline-block;
  margin: 4px;
  padding: 6px 12px;
  border-radius: 4px;
  background-color: gray;
  color: white;
  cursor: pointer;
}
</style> -->

<!-- 컴포넌트 emit -->
<!-- <template>
  <div class="btn">
    <slot></slot>
  </div>
  <h1 @click="$emit('click', $event)">ABC</h1>
  <input 
    type="text"
    v-model="msg" />
</template>

<script>
export default {
  // 이벤트를 원하는 이름을 사용해도 상관 없고 정확하게 emits옵션에서 받아서
  // (특정 이벤트를 상속 받아서) emits에 연결하여 어디에서 어떻게 사용할 것인지를 $emit()을 정의해준다.
  // 부모요소에 연결되어 있는 이벤트를 실행할 수 있다.
  emits: [
    'click',
    'changeMsg'
  ],
  data() {
    // 양 방향 데이터 바인딩으로 갱신이 된다.
    return {
      msg: ''
    }
  },
  watch: {
    msg() {
      this.$emit('changeMsg', this.msg)
    }
  }
}
</script>

<style scoped>
.btn {
  display: inline-block;
  margin: 4px;
  padding: 6px 12px;
  border-radius: 4px;
  background-color: gray;
  color: white;
  cursor: pointer;
}
</style> -->

<!-- 컴포넌트 slot -->
<!-- Fallback Contents: slot태그 사이에 내용이 없을때 출력되는 기본 내용 -->
<!-- slot부분에 name속성으로 정확한 위치를 조정할 수 있다. 이를 이름을 갖는 슬롯이라 한다. -->
<!-- <template>
  <div class="btn"> -->
    <!-- <slot>Apple</slot> -->
    <!-- <slot name="icon"></slot>
    <slot name="text"></slot>
  </div>
</template>

<script>
export default {
}
</script>

<style scoped>
.btn {
  display: inline-block;
  margin: 4px;
  padding: 6px 12px;
  border-radius: 4px;
  background-color: gray;
  color: white;
  cursor: pointer;
}
</style> -->