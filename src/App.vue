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

function makeLine() {
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

function clearText() {
  text.value = "";
}

function generatePhrase() {
  const phrases = [
    "Acredite em você e tudo será possível.",
    "O sucesso é a soma de pequenos esforços repetidos diariamente.",
    "A persistência é o caminho do êxito.",
    "Você é mais forte do que imagina, acredite.",
    "A verdadeira coragem é seguir em frente mesmo com medo.",
    "Não deixe que o medo de errar impeça você de tentar.",
    "Cada desafio é uma oportunidade para crescer.",
    "A mudança começa no momento em que você decide agir.",
    "O fracasso é uma lição, não um destino.",
    "O único limite para o seu sucesso é a sua mente.",
    "Tudo o que você sempre quis está do outro lado do medo.",
    "Grandes coisas nunca vêm de zonas de conforto.",
    "Acredite no poder dos seus sonhos e siga em frente.",
    "O sucesso não é o fim, o fracasso não é fatal: é a coragem de continuar que conta.",
    "Se você pode sonhar, você pode realizar.",
    "A única pessoa que você deve se esforçar para ser melhor do que é a pessoa que você foi ontem.",
    "Desafios são o que tornam a vida interessante, e superá-los é o que dá significado à vida.",
    "Não é sobre ser o melhor, é sobre ser melhor do que você foi ontem.",
    "Você não pode mudar o passado, mas pode escrever um novo futuro.",
    "As coisas boas acontecem para quem acredita, melhores para quem é paciente, e as melhores para quem não desiste.",
    "A vida é 10% o que acontece e 90% como reagimos a isso.",
    "Se você pode sonhar, você pode fazer.",
    "A única maneira de fazer um ótimo trabalho é amar o que você faz.",
    "O sucesso é a soma de pequenos esforços repetidos dia após dia.",
    "Não conte os dias, faça os dias contarem.",
    "A felicidade não é algo pronto. Ela vem de suas próprias ações.",
    "O único limite para o nosso amanhã é nossas dúvidas de hoje.",
    "Acredite que você pode e você já está no meio do caminho.",
    "Grandes coisas nunca vêm de zonas de conforto.",
    "O futuro pertence àqueles que acreditam na beleza de seus sonhos.",
    "A vida é uma aventura ousada ou não é nada.",
    "A única pessoa que você está destinado a se tornar é a pessoa que você decide ser.",
    "Dificuldades preparam pessoas comuns para destinos extraordinários.",
    "Não importa quão devagar você vá, contanto que você não pare.",
    "As melhores e mais belas coisas do mundo não podem ser vistas ou até ouvidas, mas devem ser sentidas com o coração.",
    "Você é o arquiteto do seu próprio destino.",
    "O sucesso não é a chave para a felicidade. A felicidade é a chave para o sucesso.",
    "A vida é como andar de bicicleta. Para ter equilíbrio, você precisa continuar em movimento.",
    "Faça da sua vida um sonho, e de um sonho, uma realidade.",
    "O amanhã pertence àqueles que se preparam para ele hoje.",
    "A vida é um eco. O que você envia, volta.",
    "Cada dia é uma nova oportunidade para mudar sua vida.",
    "A verdadeira felicidade vem de dentro.",
    "Acredite em si mesmo e todo o resto virá naturalmente.",
    "As estrelas não podem brilhar sem escuridão.",
    "O amor é a chave que abre as portas da felicidade.",
    "Faça o que você ama e nunca terá que trabalhar um dia na sua vida.",
    "A única maneira de alcançar o impossível é acreditar que é possível.",
    "O sol sempre brilha depois da tempestade.",
    "Você é mais forte do que imagina.",
    "Sonhe grande e ouse falhar.",
    "A gratidão transforma o que temos em suficiente.",
    "Seja a mudança que você deseja ver no mundo.",
    "Viva a vida ao máximo e concentre-se no positivo.",
    "A vida é como um livro; se você não viaja, você lê apenas uma página.",
    "O sucesso é a soma de pequenos esforços repetidos dia após dia.",
    "A felicidade é uma escolha, não um resultado.",
    "Cada dia é uma nova chance para se tornar quem você deseja ser.",
    "O caminho para o sucesso é sempre em construção.",
    "A vida é feita de escolhas; escolha ser feliz.",
    "Seu potencial é limitado apenas pela sua imaginação.",
  ];

  const phrase = phrases[Math.floor(Math.random() * phrases.length)];
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
            :class="{
              'bolder-text': isBolder,
              'italic-text': isItalic,
              'line-text': haveLine,
            }"
          >
            {{ text ? text : "Seu texto irá aparecer aqui" }}
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
          <div class="act-bolder" @click="makeBolder">B</div>

          <div class="act-italic" @click="makeItalic">I</div>

          <div class="act-line" @click="makeLine">A</div>
        </div>
      </div>
    </div>
  </div>
</template>

<style></style>
