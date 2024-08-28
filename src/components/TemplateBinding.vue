<script>
export default {
  name: 'TemplateBinding',
  data() {
    return {
      fondo: '',
      texto: '',
      mostrar: '',
      borde: '',
      contenido: '',
      opaco: '',
      typoSelected: '',
      typoFamily: ['cursive', 'fantasy', 'monospace', 'serif', 'initial'],
      tamanoTyposelected: '',
      tamanoTypo: [
        { value: '1rem', label: 'Pequeño' },
        { value: '2rem', label: 'Mediano' },
        { value: '3rem', label: 'Grande' }
      ]
    }
  }
}
</script>
<template>
  <h1 class="text-center">Custom template</h1>
  <div class="container">
    <form>
      <div class="form-group">
        <label for="fondo">Color de fondo</label>
        <input type="color" id="fondo" v-model="fondo" class="form-control" />
      </div>
      <div class="form-group">
        <label for="texto">Color de texto</label>
        <input type="color" id="texto" v-model="texto" class="form-control" />
      </div>
      <div class="form-group row">
        <label for="mostrar">Mostrar texto</label>
        <input type="checkbox" name="mostrar" v-model="mostrar" />
      </div>
      <div class="form-group">
        <label for="borde">Borde</label>
        <input type="range" name="borde" id="borde" min="0" max="50" v-model="borde" />
      </div>
      <div class="form-group">
        <label for="contenido"> Contenido textual</label>
        <textarea name="contenido" id="contenido" v-model="contenido"></textarea>
      </div>
      <div class="form-group column custom-select-wrapper">
        <label for="typo">Tipografía</label>
        <select name="typo" id="typo" v-model="typoSelected" class="custom-select">
          <option value="" disabled>Selecciona una tipografía</option>
          <option v-for="typo in typoFamily" :key="typo" :value="typo">
            {{ typo }}
          </option>
        </select>
      </div>
      <div class="form-group row">
        <label for="opaco">Opaco</label>
        <input type="checkbox" name="opaco" v-model="opaco" />
      </div>
      <div class="form-group">
        <label class="w-100" for="tamanoTypo">Tamaño de letra</label>
        <div class="form-group radio row">
          <div v-for="tamano in tamanoTypo" :key="tamano.value" class="row">
            <label :for="tamano.value">{{ tamano.label }}</label>
            <input
              type="radio"
              :name="tamano.value"
              :id="tamano.value"
              :value="tamano.value"
              class="radio"
              v-model="tamanoTyposelected"
            />
          </div>
        </div>
      </div>
    </form>

    <div
      class="custom"
      :style="{
        backgroundColor: fondo,
        color: texto,
        borderRadius: `${borde}%`,
        fontFamily: typoSelected,
        fontSize: tamanoTyposelected
      }"
      :class="{
        opaco: opaco
      }"
    >
      <p v-show="mostrar">{{ contenido }}</p>
    </div>
  </div>
</template>
<style>
.text-center {
  text-align: center;
  padding-bottom: 3rem;
}
.container {
  display: flex;
  justify-content: center;
  align-items: center;
  column-gap: 80px;
}
form {
  display: flex;
  flex-direction: column;
  color: rgb(57, 57, 54);
  justify-content: center;
  font-weight: 500;
  padding: 10px;
  background-color: rgb(219, 234, 249);
  width: 400px;
  border-radius: 10px;
  box-shadow: 6px 6px 8px -3px rgba(20, 20, 20, 0.43);
}
.form-group {
  margin-block: 10px;
}
.row {
  display: flex;
  gap: 10px;
}
.column {
  display: flex;
  flex-direction: column;
}

.form-control {
  border: none;
  width: 100%;
  margin-block: 10px;
  cursor: pointer;
}

.custom {
  width: 400px;
  height: 400px;
  display: flex;
  align-items: center;
  justify-content: center;
}
.opaco {
  opacity: 0.4;
}
label {
  margin-bottom: 10px;
}

/* Estilizar el input de rango */
input[type='range'] {
  -webkit-appearance: none;
  appearance: none;
  background: transparent;
  cursor: pointer;
  width: 100%;
  border: none;
}

/* Remover default focus */
input[type='range']:focus {
  outline: none;
}
/******** Chrome, Safari, Opera and Edge Chromium styles ********/
input[type='range']::-webkit-slider-runnable-track {
  background-color: #bbb8b8;
  border-radius: 0.5rem;
  height: 0.5rem;
}

input[type='range']::-webkit-slider-thumb {
  -webkit-appearance: none;
  appearance: none;
  margin-top: -4px;
  background-color: #2e9375;
  border-radius: 0.5rem;
  height: 1rem;
  width: 1.5rem;
}

input[type='range']:focus::-webkit-slider-thumb {
  outline: 1px solid #2e9375;
  outline-offset: 0.125rem;
}

/*********** Firefox styles ***********/
input[type='range']::-moz-range-track {
  background-color: #ccc;
  border-radius: 0.5rem;
  height: 0.5rem;
}

/* Estilizando el chexkbox */
input[type='checkbox'],
input[type='radio'] {
  appearance: none;
  -webkit-appearance: none;
  -moz-appearance: none;
  position: relative;
  width: 20px;
  height: 20px;
  margin-right: 10px;
  border: none;
  border-radius: 3px;
  cursor: pointer;
}

input[type='checkbox'] {
  background-color: #2e9375;
  border: 1px solid #ccc;
}
input[type='checkbox']:checked {
  background-color: #2e9375;
}

input[type='checkbox']:checked::after {
  content: '';
  position: absolute;
  left: 6px;
  top: 1px;
  width: 4px;
  height: 12px;
  border: solid white;
  border-width: 0 2px 2px 0;
  transform: rotate(45deg);
}

/* Estilizar el radio */
input[type='radio'] {
  background-color: #2e9375;
  border: 1px solid #ccc;
  border-radius: 50%;
}

input[type='radio']:checked {
  background-color: #2e9375;
}

input[type='radio']:checked::after {
  content: '';
  position: absolute;
  left: 3px;
  top: 3px;
  width: 12px;
  height: 12px;
  background-color: white;
  border-radius: 50%;
}
textarea {
  width: 100%;
  height: 100px;
  padding: 10px 15px;
  margin-top: 5px;
  box-sizing: border-box;
  border: 2px solid #ccc;
  border-radius: 4px;
  background-color: #f8f8f8;
  resize: none;
}
/* Estilizando el select */
.custom-select-wrapper {
  position: relative;
  display: inline-block;
  width: 100%;
}

.custom-select {
  appearance: none;
  background-color: #2e9375;
  color: white;
  padding: 10px 15px;
  font-size: 16px;
  border-radius: 5px;
  border: 1px solid #ccc;
  cursor: pointer;
  width: 100%;
  box-sizing: border-box;
}

/* Flecha personalizada */
.custom-select-wrapper::after {
  content: '▼';
  position: absolute;
  right: 15px;
  top: 70%;
  transform: translateY(-50%);
  pointer-events: none;
  color: white;
  font-size: 12px;
}

.custom-select:focus {
  border-color: #1e6f57;
  outline: none;
}

.custom-select option {
  background-color: white;
  color: black;
}
</style>
