<template>
  <div id="Propiedades">
    <div v-if="error">{{ error }}</div>
    <div v-else class="grilla">
      <div v-for="propiedad in propiedades" :key="propiedad.id">
        <div class="card" :class="propiedad.comuna">
          <figure class="imagen">
            <div class="dividendo">
              <span>Hasta 3 dividendos</span>
            </div>
            <template v-if="propiedad.imagen == null">
              <img src="https://picsum.photos/350/250" />
            </template>
            <template v-else>
              <img :src="path + propiedad.imagen.url" alt="" />
            </template>
            <div class="entrega">
              <span>{{ propiedad.tipoVenta }}</span>
            </div>
          </figure>
          <div class="card-content">
            <div class="titulo">
              <h2>
                {{ propiedad.nombre }}
                <br />Alto el Rincon
              </h2>
            </div>
            <span class="separator"></span>
            <div class="valor">
              <div class="ahora">
                <h2>
                  <b class>{{ propiedad.valorActual }} UF</b>
                </h2>
                Ahora
              </div>
              <div class="antes">
                <h2 class="subrayado">{{ propiedad.valorPasado }} UF</h2>
                Antes
              </div>
            </div>
            <div class="dscto">
              <h2>Hasta {{ propiedad.dscto }}% Dscto.</h2>
            </div>
            <div class="tipo">
              <h3>{{ propiedad.tipo }}</h3>
              <br />
            </div>
            <div class="comprar">
              <a
                href="https://mialborada.cl/proyectos/condominio-alto-el-rincon/"
                class="comprar"
              >
                Ver Más
              </a>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "cardPropiedades",
  data() {
    return {
      propiedades: [],
      error: null,
      path: "https://strapi-alborada.herokuapp.com",
    };
  },

  // path para localhost = http://localhost:1337
  // Path para Heroku Produccion = https://strapi-alborada.herokuapp.com/

  async mounted() {
    try {
      const response = await axios.get(
        "https://strapi-alborada.herokuapp.com/propiedades"
      );
      this.propiedades = response.data;
    } catch (error) {
      this.error = error;
    }
  },
};
</script>

<style lang="scss">
$bordes: 8px;

@mixin bordeado {
  border-radius: $bordes;
}
@mixin bordeado-top {
  border-top-left-radius: $bordes;
  border-top-right-radius: $bordes;
}
@mixin sombreado {
  -webkit-box-shadow: 0px 15px 45px -12px rgba(22, 209, 110, 0.3);
  -moz-box-shadow: 0px 15px 45px -12px rgba(22, 209, 110, 0.3);
  box-shadow: 0px 15px 45px -12px rgba(22, 209, 110, 0.3);
}
@mixin boton($color) {
  padding: 0.5rem 1.5rem;
  background-color: $color;
  text-decoration: none;
  @include bordeado();
}

#Propiedades {
  width: 100%;
  max-width: 1200px;
  margin: 0 auto;
  margin-top: 2rem;
  .grilla {
    margin: 0 auto;
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    column-gap: 2rem;
    row-gap: 1rem;
    margin-top: 1rem;
    .card {
      border: 2px solid #16d16e;
      @include bordeado();
      @include sombreado();
      color: white;
      transition: all 0.3s ease-in-out;
      &:hover {
        transform: scale(1.1);
      }
      .imagen {
        position: relative;
        width: 100%;
        margin: 0;
        img {
          width: 100%;
          @include bordeado-top();
        }
        .dividendo {
          position: absolute;
          padding: 5px 1rem;
          background-color: #16d16d;
          color: #38205e;
        }
        .entrega {
          position: absolute;
          padding: 5px 1rem;
          bottom: 3px;
          width: 92%;
          background-color: #5109c594;
          color: white;
        }
      }
      .card-content {
        .valor {
          display: flex;
          justify-content: space-evenly;
          .antes {
            .subrayado {
              text-decoration: line-through;
            }
          }
        }
        div.comprar {
          width: 100%;
          a {
            width: 100%;
            transition: all 0.3s ease;
            @include boton(#16d16e);
            &:hover {
              background-color: hsl(120, 100%, 75%);
            }
            &:active {
              color: white;
            }
          }
        }
        .separator {
          display: inline-block;
          height: 1px;
          width: 60%;
          background-color: #16d16e;
          @include sombreado();
        }
      }
    }
  }
}
</style>
