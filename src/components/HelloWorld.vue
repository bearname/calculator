<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <p>UI kit</p>

    <ButtonText/>
    <Checkbox/>
    <Checkbox :disabled="true"/>

    <Button :text="'Кнопка'"/>
    <Button :disabled="true" :text="'Кнопка'"/>
    <div class="bg-primary">
      <button class="btn btn-secondary">Кнопка</button>
      <button class="btn btn-secondary btn-secondary-disabled">Кнопка</button>
    </div>

    <Tag/>
    <Tag :disabled="true"/>

    <Input :text="'Текст'" :placeholder="'Текст'" />
    <Input :text="'Текст'" :placeholder="'Текст'" :disabled="true" />
  </div>
</template>

<script>
import ButtonText from "./input/ButtonText";
import Checkbox from "./input/Checkbox";
import Button from "./input/Button";
import Tag from "./input/Tag";
import Input from "./input/Input";
export default {
  name: 'HelloWorld',
  components: { Input, Tag, Button, Checkbox, ButtonText },
  props: {
    msg: String
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
