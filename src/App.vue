<script setup>
import { ref } from "vue";

const text = ref("");
const isBolder = ref(false);
const isItalic = ref(false);
const haveLine = ref(false);
const font = ref("");
const color = ref("#A825E5");
const size = ref(null);

function changeFont(event) {
  font.value = event.target.value;
}

function makeBolder() {
  isBolder.value = !isBolder.value;
}

function makeItalic() {
  isItalic.value = !isItalic.value;
}

function makeLine(){
  haveLine.value = !haveLine.value;

}

function changeSize(event) {
  size.value = event.target.value;
}

function changeColor(event) {
  color.value = event.target.value;
}

function copyText() {
  if (text.value) {
    navigator.clipboard
      .writeText(text.value)
      .then(() => {
        alert("Texto copiado com sucesso!");
      })
      .catch((err) => {
        alert("Erro ao copiar texto!");
      });
  } else {
    alert("Sem conteúdo para copiar!");
  }
}

function clearText(){
  text.value = '';
}

</script>

<template>
  <div class="container">
    <div class="main"> 

    <div class="show-text">
      <p
        class="text-content"
        :style="{ fontFamily: font, fontSize: size, color: color }"
        :class="{ 'bolder-text': isBolder, 'italic-text': isItalic, 'line-text':haveLine }"
      >
        {{ text ? text : 'Seu texto irá aparecer aqui'  }}
      </p>
    </div>
<div class="buttons">
    <div class="copy">
        <button @click="copyText">Copiar</button>
      </div>

      <div class="clear">
        <button @click="clearText">Limpar</button>
      </div>
    </div>
    <div class="textarea">
      <textarea
        name="textarea"
        id="text-area"
        class="text-area"
        v-model="text"
      ></textarea>
    </div>
    <div class="actions">

<div class="select-actions"> 
  <div class="fonts">
    <label for="text">Fonte</label>
    <select @change="changeFont">
      <option value=""></option>
      <option value="'Impact'">Impact</option>
      <option value="'Verdana'">Verdana</option>
      <option value="'Arial'">Arial</option>
      <option value="'Courier New'">Courier New</option>
      <option value="'Times New Roman'">Times New Roman</option>
    </select>
  </div>

<div class="size">
  <label for="select">Tamanho</label>
  <select @change="changeSize">
    <option value="30px">30 Pixels</option>
    <option value="40px">40 Pixels</option>
    <option value="50px">50 Pixels</option>
    <option value="80px">80 Pixels</option>
    <option value="100px">100 Pixels</option>
  </select>
</div>

<div class="color">
  <label for="text">Cor</label>
  <input
    v-model="color"
    type="color"
    value="#ff0000"
    @change="changeColor"
  />
</div>
</div>

<div class="click-actions"> 
  <div class="act-bolder" @click="makeBolder">
    B
  </div>

  <div class="act-italic" @click="makeItalic">I</div>

  <div class="act-line" @click="makeLine">A</div>
</div>
</div>
</div>
  </div>
</template>

<style></style>
