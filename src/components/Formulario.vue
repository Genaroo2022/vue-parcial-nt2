<template>
  <section class="card">
    
    <form>
      <div class="form-group">
        <input type="text" v-model="nombre" class="form-control" />
        <p>Cantidad caracteres = {{ cantidadCaracteres }}</p>
        <ol>
          <li>{{ codificado }} (codificado)</li>
          <li>{{ mayuscula }} (mayuscula)</li>
          <li>{{ minuscula }} (minuscula)</li>
          <li>{{ intercaladoMayuscula }} (mayuscula / minuscula)</li>
          <li>{{ intercaladoMinuscula }} (minuscula / mayuscula)</li>
        </ol>
      </div>
    </form>
  </section>
  
  <br>
<p>Respuestas: 1:C - 2:C - 3:A</p>
</template>

<script>
export default {
  name: 'formulario',
  data() {
    return {
      nombre: ''
    };
  },
  computed: {
    cantidadCaracteres() {
      return this.nombre.length;
    },
    codificado() {
      const reemplazo = { a: 'u', e: 'o', i: 'i', o: 'e', u: 'a' };
      return this.nombre
        .toLowerCase()
        .split('')
        .map(c => reemplazo[c] || c)
        .join('');
    },
    mayuscula() {
      return this.nombre.toUpperCase();
    },
    minuscula() {
      return this.nombre.toLowerCase();
    },
    intercaladoMayuscula() {
      return this.nombre
        .split('')
        .map((c, i) =>
          i % 2 === 0 ? c.toUpperCase() : c.toLowerCase()
        )
        .join('');
    },
    intercaladoMinuscula() {
      return this.nombre
        .split('')
        .map((c, i) =>
          i % 2 === 0 ? c.toLowerCase() : c.toUpperCase()
        )
        .join('');
    }
  }
};
</script>

<style scoped>
.card {
  padding: 20px;
  font-family: sans-serif;
}
</style>
