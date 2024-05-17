<template>
  <div id="app">
    <div class="container py-5">
      <div class="row">
        <!-- Columna de cambios -->
        <div class="container-cambios col-6 container py-5">
          <form class="d-flex flex-column">
            <h2 class="text-center pb-2">Cambia texto y color a tu gusto!</h2>
            <!-- cambio de fondo -->
            <label for="">Color de fondo</label>
            <input type="color" id="colorFondo" v-model="colorFondo"><br>

            <!-- cambio colo de texto -->
            <label for="">Color de texto</label>
            <input type="color" id="colorTexto" v-model="colorTexto"><br>

            <!-- checkbox mostrar texto -->
            <div class="pb-2">
              <label class="mx-2" for="">Mostrar texto</label>
              <input type="checkbox" id="mostrarTexto" v-model="mostrarTexto">
            </div>

            <!-- Cambio rango de borde -->
            <div>
              <label for="">Borde</label><br>
              <input type="range" id="rangeborde" name="rangeborde" min="0" max="50" step="1" v-model="borde">
            </div>

            <!-- text area para contenido -->
            <div>
              <label for="contenidoTextual">Contenido textual</label><br>
              <textarea name="text" id="contenidoTextual" cols="60" rows="3" v-model="contenidoTextual"
                class="form-control"></textarea>
            </div>

            <!-- opciones para tipografia -->
            <div>
              <label class="pb-2" for="tipografias">Tipografías</label>
              <br>
              <select name="tipografias" id="tipografias" v-model="tipografias">
                <option :value="tipografia" v-for="(tipografia, index) in tipografiaArray" :key="index">{{ tipografia }}
                </option>
              </select>
            </div>

            <!-- check box opaco -->
            <div class="py-3">
              <label class="mx-2" for="">Opaco</label>
              <input type="checkbox" id="opaco" v-model="opaco">
            </div>

            <!-- seleccion de tamaño de letra -->
            <div>
              <label class="pb-2" for="">Tamaño Letra</label>
              <div class="row">
                <div class="col-4">
                  <input class="mx-2" type="radio" id="pequeño" name="fav_language" value="pequeno"
                    v-model="tamanoLetra">
                  <label for="pequeño">Pequeño</label><br>
                </div>
                <div class="col-4">
                  <input class="mx-2" type="radio" id="mediano" name="fav_language" value="mediano"
                    v-model="tamanoLetra">
                  <label for="mediano">Mediano</label><br>
                </div>
                <div class="col-4">
                  <input class="mx-2" type="radio" id="grande" name="fav_language" value="grande" v-model="tamanoLetra">
                  <label for="grande">Grande</label>
                </div>
              </div>
            </div>

          </form>
        </div>

        <!-- Columna del resultado -->
        <div class="container-resultado col-6 container py-5 d-flex align-items-center justify-content-center">
          <div id="" class="h-75 w-75 d-flex align-items-center justify-content-center" :style="{
            borderRadius: borde + '%',
            backgroundColor: colorFondo,
            opacity: opaco ? '0.5' : '1'
          }">
            <div>
              <p :style="{
                color: colorTexto,
                fontStyle: tipografias
              }" :class="[tamanoLetra == 'grande' ? largeClass : tamanoLetra == 'pequeno' ? smallClass : mediumClass]"
                v-show="mostrarTexto">{{ contenidoTextual }}</p>
            </div>
          </div>

        </div>

      </div>
    </div>

  </div>
</template>

<script>
export default {
  name: 'App',
  components: {

  },
  data() {
    return {
      colorFondo: "background-color: rgb(255, 255, 255)",
      colorTexto: "color: rgb(49, 147, 49)",
      mostrarTexto: true,
      borde: 0,
      contenidoTextual: "",
      tipografias: "normal",
      opaco: false,
      tamanoLetra: "",
      tipografiaArray: [
        "italic", "normal", "oblique"
      ],
      smallClass: "smallText",
      mediumClass: "mediumText",
      largeClass: "largeText",
    }
  },
}
</script>

<style>
.container-cambios {
  background-color: rgb(49, 147, 49);
}


.smallText {
  font-size: 16px;
}

.mediumText {
  font-size: 24px;
}

.largeText {
  font-size: 32px;
}
</style>
