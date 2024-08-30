<script>
export default {
  name: 'FormRenderizado',
  data() {
    return {
      fondoColor: '#000000',
      textColor: '',
      mostrarText: '',
      tamanoBorde: '',
      contenidoTextual: '',
      tipografia: [
        { label: 'Cursiva', value: 'italicText' },
        { label: 'Negrita', value: 'boldText' }
      ],
      tipografiaSelected: '',
      opaco: '',
      tamanoLetraSelected: '',
      tamanoLetra: [
        { label: 'Pequeño', value: 'pequeno' },
        { label: 'Mediano', value: 'mediano' },
        { label: 'Grande', value: 'grande' }
      ]
    }
  }
}
</script>
<template>
  <div class="container">
    <form class="form">
      <label for="colorFondo">Color de Fondo</label>
      <input type="color" id="colorFondo" v-model="fondoColor" />

      <label for="colorTexto">Color de Texto</label>
      <input type="color" id="colorTexto" v-model="textColor" />

      <div class="inRow">
        <label for="mostrarTexto">Mostrar Texto</label>
        <input type="checkbox" v-model="mostrarText" id="mostrarTexto" />
      </div>

      <label for="border">Borde</label>
      <input type="range" min="5" max="40" value="5" id="border" v-model="tamanoBorde" />

      <label for="contenido">Contenido Textual</label>
      <textarea id="contenido" v-model="contenidoTextual"></textarea>

      <label for="tipografia">Tipografia</label>
      <select name="tipografia" id="tipografia" v-model="tipografiaSelected">
        <option v-for="option in tipografia" :key="option.value" :value="option.value">
          {{ option.label }}
        </option>
      </select>

      <div class="inRow">
        <label for="opacidad">Opaco</label>
        <input type="checkbox" v-model="opaco" id="opacidad" />
      </div>
      <div class="inColumn">
        <label for="tamanoLetra">Tamaño de Letra</label>
        <div class="inRow" v-for="tamano in tamanoLetra" :key="tamano.value">
          <label :for="tamano">{{ tamano.label }}</label>
          <input
            type="radio"
            :value="tamano.value"
            v-model="tamanoLetraSelected"
            :id="tamano.label"
            :name="tamano.value"
          />
        </div>
      </div>
    </form>

    <div
      id="cuadroDeMuestra"
      :style="{
        backgroundColor: fondoColor,
        color: textColor,
        borderRadius: `${tamanoBorde}%`
      }"
    >
      <p v-show="mostrarText" :class="tipografiaSelected">{{ contenidoTextual }}</p>
    </div>
  </div>
</template>
<style scoped>
.container {
  display: flex;
}
.inRow {
  display: flex;
  padding: 1.5rem 0;
  justify-content: space-between;
}
.inColumn {
  display: flex;
  flex-direction: column;
  padding: 0 1.5rem;
}
.form {
  background-color: #2f4f4f;
  display: flex;
  flex-direction: column;
  align-items: start;
  padding-inline: 2.5rem;
  padding-block: 2rem;
}
label {
  color: #ffffff;
}
input {
  width: 100%;
  margin-bottom: 1rem;
}

#cuadroDeMuestra {
  height: 400px;
  width: 400px;
  text-align: center;
}
</style>
