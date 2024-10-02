<script setup>
import { ref } from "vue";

const text = ref("");
const isBolder = ref(false);
const isItalic = ref(false);
const haveLine = ref(false);
const font = ref("");
const color = ref("#fff");
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

function generatePhrase(){
  const phrases = [  "Acredite em você e tudo será possível.",
  "O sucesso é a soma de pequenos esforços repetidos diariamente.",
  "A persistência é o caminho do êxito.",
  "Você é mais forte do que imagina, acredite.",
  "A verdadeira coragem é seguir em frente mesmo com medo.",
  "Não deixe que o medo de errar impeça você de tentar.",
  "Cada desafio é uma oportunidade para crescer.",
  "A mudança começa no momento em que você decide agir.",
  "O fracasso é uma lição, não um destino.",
  "O único limite para o seu sucesso é a sua mente.",   "Tudo o que você sempre quis está do outro lado do medo.",
  "Grandes coisas nunca vêm de zonas de conforto.",
  "Acredite no poder dos seus sonhos e siga em frente.",
  "O sucesso não é o fim, o fracasso não é fatal: é a coragem de continuar que conta.",
  "Se você pode sonhar, você pode realizar.",
  "A única pessoa que você deve se esforçar para ser melhor do que é a pessoa que você foi ontem.",
  "Desafios são o que tornam a vida interessante, e superá-los é o que dá significado à vida.",
  "Não é sobre ser o melhor, é sobre ser melhor do que você foi ontem.",
  "Você não pode mudar o passado, mas pode escrever um novo futuro.",
  "As coisas boas acontecem para quem acredita, melhores para quem é paciente, e as melhores para quem não desiste."];

  const phrase =  phrases[Math.floor(Math.random() * phrases.length)];
  text.value = phrase;
}

</script>

<template>
  <div class="container">
    <div class="main"> 

      <div class="border">
    <div class="show-text">
      <p
        class="text-content"
        :style="{ fontFamily: font, fontSize: size, color: color }"
        :class="{ 'bolder-text': isBolder, 'italic-text': isItalic, 'line-text':haveLine }"
      >
        {{ text ? text : 'Seu texto irá aparecer aqui'  }}
      </p>
    </div>
  </div>
<div class="buttons">

  <div class="generate">
        <button @click="generatePhrase">Gerar frase</button>
      </div>

    <div class="copy">
        <button @click="copyText">Copiar</button>
      </div>

      <div class="clear">
        <button @click="clearText">Limpar</button>
      </div>

    </div>
    <div class="textarea">
      <label for="text">Crie uma frase.</label>
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
