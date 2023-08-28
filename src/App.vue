<template>
<section>
  <div id="titulo">
    <h1 style="margin: 0; font-family:'Gill Sans', 'Gill Sans MT', Calibri, 'Trebuchet MS', sans-serif;">🕹️ NEW HORIZON</h1>
    <button id="carrito" style="font-size: 150%;" @click="showModal = true">🛒</button>
  </div>
  <div v-if="showModal" class="modal" >
  <div class="modal-content" @click="cerrarModalClicExterior">
    <h1 style="font-size: 30px; width: 100%; background-color: purple; margin: 0; border-radius: 35px;">Carrito de Compras</h1>
    <table>
    <thead>
      <tr>
        <th></th>
        <th>Producto</th>
        <th>Cantidad</th>
        <th>Precio</th>
        <th></th>
      </tr>
    </thead>
    <tbody>
      <tr v-for="(producto, index) in carrito" :key="index">
        <td><img :src="producto.img" :alt="producto.nombre" class="imagen-producto"></td>
        <td>{{ producto.nombre }}</td>
        <td>{{ producto.cantidad }}</td>
        <td>${{ producto.precio.toLocaleString("es-ES", {
          style: "currency",
          currency: "COP",
          minimumFractionDigits: 0,
          maximumFractionDigits: 2,
        }) }}</td>
        <td><button @click="eliminarCarrito(index)" style="background-color: transparent; border: 0; cursor: pointer; font-size: x-large;" id="equis">❌</button></td>
      </tr>
    </tbody>
  </table>
  <div style="display: flex; flex-direction: row; justify-content: space-between; align-items: center;">
    <div class="total-container">
      <span style="font-size: 30px;">Total: </span>
      <span style="font-size: 20px;"> ${{ calcularTotal().toLocaleString("es-ES", {
        style: "currency",
        currency: "COP",
        minimumFractionDigits: 0,
        maximumFractionDigits: 2,
        useGrouping: true
      }) }}</span>
    </div>
    <button @click="showModal = false" style="background-color: purple; border: 0; cursor: pointer; border-radius: 15px; height: 45px; color: white; width: 85px; font-size: large;">Cerrar</button>
  </div>
  </div>
</div>
  <div >
    <div id="busqueda" style="margin-top: 4%;"></div>
    <div id="cuadro-busqueda">
      <h1 id="conoce" style="grid-column: 1/2; margin-left: 100px;">!CONOCE NUEVOS MUNDOS¡</h1>
      <h2 id="interesado" style="grid-column: 1/2; margin-left: 100px;">Tienda de videojuegos digitales</h2> <br>
    </div>
  </div>
  <div class="contitulos" style="margin-top: 4%;">
    <div id="masVendidos">
      <h1 style="font-size: 40px;">Los mas vendidos</h1>
      <h4>Explora los videojuegos mas populares</h4>
    </div>
  </div>
  <div class="cards">
    <div v-for="(item, index) in imagenes1" :key="index" class="card">
      <div class="face front">
        <img :src="item.img" alt="">
      </div>
      <div class="face back" style="color: white;">
        <h1>{{ item.nombre }}</h1>
        <p style="padding: 30px; text-align: justify; color: rgb(201, 201, 201);"> {{ item.desc }} </p>
        <button class="botonAgg" @click="agregarAlCarrito(item)">
          <h2 style="color: rgb(201, 201, 201);">$ {{ (item.precio).toLocaleString("es-ES", {
              style: "currency",
              currency: "COP",
              minimumFractionDigits: 0,
              maximumFractionDigits: 2,
            }) }}</h2>
            <h1 class="btnAgg">🛒</h1>
        </button>
      </div>
    </div>
  </div>
  <div class="contitulos">
    <div id="masVendidos">
      <h1 style="font-size: 40px;">Los mejores de rol</h1>
      <h4>Los amantes del rol juegan esto</h4>
    </div>
  </div>
  <div class="cards">
    <div v-for="(item, index) in imagenes2" :key="index" class="card">
      <div class="face front">
        <img :src="item.img" alt="">
      </div>
      <div class="face back" style="color: white; ">
        <h1>{{ item.nombre }}</h1>
        <p style="padding: 30px; text-align: justify; color: rgb(201, 201, 201);"> {{ item.desc }} </p>
        <button class="botonAgg" @click="agregarAlCarrito(item)">
          <h2 style="color: rgb(201, 201, 201);">$ {{ (item.precio).toLocaleString("es-ES", {
              style: "currency",
              currency: "COP",
              minimumFractionDigits: 0,
              maximumFractionDigits: 2,
            }) }}</h2>
            <h1 class="btnAgg">🛒</h1>
        </button>
      </div>
    </div>
  </div>
  <div class="contitulos">
    <div id="masVendidos">
      <h1 style="font-size: 40px;">Los mejores para jugar Online</h1>
      <h4>Para jugar con tus amigos</h4>
    </div>
  </div>
  <div class="cards" style="padding-bottom: 45px;">
    <div v-for="(item, index) in imagenes3" :key="index" class="card">
      <div class="face front">
        <img :src="item.img" alt="">
      </div>
      <div class="face back" style="color: white;">
        <h1>{{ item.nombre }}</h1>
        <p style="padding: 30px; text-align: justify; color: rgb(201, 201, 201);"> {{ item.desc }} </p>
        <button class="botonAgg" @click="agregarAlCarrito(item)">
          <h2 style="color: rgb(201, 201, 201);">$ {{ (item.precio).toLocaleString("es-ES", {
              style: "currency",
              currency: "COP",
              minimumFractionDigits: 0,
              maximumFractionDigits: 2,
            }) }}</h2>
            <h1 class="btnAgg">🛒</h1>
        </button>
      </div>
    </div>
  </div>
  <div id="final">
    <h4 style="margin: 0; font-family:'Gill Sans', 'Gill Sans MT', Calibri, 'Trebuchet MS', sans-serif;">Creado por Luis Felipe Pineda Meneses</h4>
    <div style="align-items: center; display: flex; height: 100%; gap: 20px;">
      <img src="https://th.bing.com/th/id/R.330becd1786bd3d7958390ab98fdfef5?rik=Wiz4%2f0vJPdjcQg&riu=http%3a%2f%2fwww.pngall.com%2fwp-content%2fuploads%2f5%2fInstagram-Logo.png&ehk=D5ANNPTo%2fjLAW0UR1u9rms69i4BiAZ9%2fUunNikLa96Y%3d&risl=&pid=ImgRaw&r=0" alt="">
      <img src="https://th.bing.com/th/id/R.30b680f7323ad852bdd859f67ed5f952?rik=BUChTqzCmHdjbg&riu=http%3a%2f%2fsguru.org%2fwp-content%2fuploads%2f2018%2f02%2ficon-facebook-black.png&ehk=ZDm5BxOPIvzQb0K7841ckac7K958nw9U0EOK%2byVHRBs%3d&risl=&pid=ImgRaw&r=0" alt="">
      <img src="https://sguru.org/wp-content/uploads/2018/02/twitter-circled.png" alt="">
      <img src="https://i.pinimg.com/originals/88/02/74/880274abefd084cf9b89447bcc8b7782.png" alt="">
    </div>
  </div>
</section>

</template>

<script setup>
import { ref, onMounted, onUnmounted  } from 'vue';
import juego1 from './img/juego1.jfif'
import juego2 from './img/juego2.jfif'
import juego3 from './img/juego3.jfif'
import juego4 from './img/juego4.jfif'
import juego5 from './img/juego5.jfif'
import juego6 from './img/juego6.jfif'
import juego7 from './img/juego7.jfif'
import juego8 from './img/juego8.jfif'
import juego9 from './img/juego9.jfif'
import juego10 from './img/juego10.jfif'
import juego11 from './img/juego11.jfif'
import juego12 from './img/juego12.jfif'

const showModal = ref(false);

const cerrarModal = () => {
  showModal.value = false;
};

const cerrarModalClicExterior = (event) => {
  if (event.target.classList.contains('modal')) {
    cerrarModal();
  }
};

onMounted(() => {
  document.addEventListener('click', cerrarModalClicExterior);
});

onUnmounted(() => {
  document.removeEventListener('click', cerrarModalClicExterior);
});

const imagenes1 = ref([
  {img: juego1, nombre:"Grand Theft Auto 5", desc: "GTA 5 es un videojuego de acción-aventura de mundo abierto desarrollado por Rockstar North y distribuido por Rockstar Games123. El juego nos lleva a Los Santos, una ciudad inspirada en Los Ángeles, donde controlamos a tres personajes: Franklin, Michael y Trevor, cuyas vidas se entrelazan en una trama de crimen, acción y humor13.",precio: 130000},
  {img: juego2, nombre:"FIFA 22", desc: "FIFA 22 es la penultima entrega de la serie FIFA desarrollada por EA Canada y publicada por Electronic Arts. El juego te lleva de vuelta al mundo del fútbol internacional, ofreciendo imágenes y mecánicas de juego mejoradas, acercando todavía más los partidos virtuales a sus contrapartes de la vida real." ,precio: 150000},
  {img: juego3, nombre: "Borderlands 3", desc: "Borderlands 3 es un juego cooperativo de disparos en primera persona desarrollado por Gearbox Software y publicado por 2K Games. El juego se centra en explorar entornos de mundo abierto de las Tierras Fronterizas titulares y matar enemigos con una variedad de armas." ,precio: 110000},
  {img: juego4, nombre: "Minecraft", desc: "Minecraft Java Edition es una de las dos versiones oficiales del juego de supervivencia sandbox, lanzado en 2011 por Mojang Studios para PC. Entra en el increíblemente enorme mundo de los cubos y diséñalo como quieras. Selecciona un modo relajado y creativo o lucha contra los monstruos en el modo Supervivencia. Solo o en multijugador, en Minecraft puedes hacer cualquier cosa.", precio: 130000}
])

const imagenes2 = ref([
  {img: juego5, nombre: "The Witcher 3", desc: "El protagonista del juego, Geralt de Rivia, es el brujo titular, cazador de monstruos, que se embarca en la búsqueda para salvar a su hija adoptiva de la Cacería Salvaje, una banda de guerreros que quieren usarla para sus propios fines. The Witcher 3 pone énfasis en la acción y la elaboración, así como en completar misiones secundarias para varios NPC, que recompensan al jugador con oro y experiencia.", precio: 150000},
  {img: juego6, nombre: "Elden Ring", desc: "Elden Ring es un juego de rol de fantasía oscura desarrollado por FromSoftware y publicado gracias a Bandai Namco Entertainment. Descubre los secretos de Lands Between y embárcate en la misión más heroica para descubrir el propósito del artefacto mágico y tu destino. El lanzamiento de Elden Ring está programado para el año 2022.", precio: 200000},
  {img: juego7, nombre: "Hades", desc: "Hades es un juego de hack'n'slash desarrollado por Supergiant Games, el estudio conocido también por producciones como el famoso Bastion, Transistor o Pyre. El juego le da al jugador la oportunidad de visitar la mítica tierra de los muertos. El jugador toma el papel de Zagreus, el príncipe del Inframundo, hijo de Hades, que está tratando de alejarse de las garras de su padre y llegar al Monte Olimpo.", precio: 120000},
  {img: juego8, nombre: "Persona 5 Royal", desc: "Persona 5 Royal es un videojuego de rol desarrollado y publicado por Atlus. Una vez más, el jugador toma el control del protagonista sin nombre usando el nombre en clave 'Joker', el líder de un grupo conocido como Phantom Thieves, que atacan los vicios humanos ocultos dentro de sus almas. Después de limpiar su nombre al final de Persona 5, Joker regresa a la Academia Shujin para el tercer semestre, ya que la realidad comienza a desmoronarse a su alrededor.", precio: 180000}
])

const imagenes3 = ref([
  {img: juego9, nombre: "Call Of Duty Warzone", desc: "Call of Duty: Warzone es un videojuego de disparos en primera persona gratuito que se lanzó el 10 de marzo de 2020. El juego se ambienta en el mundo de Modern Warfare® y permite a los jugadores participar en batallas de hasta 150 jugadores. El juego cuenta con diferentes modos de juego, mapas, equipamiento e historia. El juego también se integra con Black Ops Cold War.", precio: 0},
  {img: juego10, nombre: "Deep Rock Galactic", desc: "Deep Rock Galactic es el original juego de disparos en primera persona desarrollado por el estudio danés Ghost Ship Games. Los jugadores asumen el papel de enanos espaciales que trabajan para extraer materias primas de las cuevas más peligrosas, donde ni siquiera los más valientes pueden aventurarse.", precio: 204000},
  {img: juego11, nombre: "Forza Horizon 5", desc: "Forza Horizon 5 es la última entrega de los juegos de simulador de conducción de mundo abierto desarrollados por Playground Games.  Forza Horizon 5 trae de vuelta la experiencia de las carreras de mundo abierto como nunca antes. Las carreteras de México están abiertas para que conduzcas los mejores autos del mundo. ", precio: 210000},
  {img: juego12, nombre: "Rocket League", desc: "Juega al fútbol con coches y domina la liga. Ponte tras el volante de un coche futurista equipado con cohetes y marca goles, o aprovecha el sistema avanzado de físicas para evitar que tus oponentes marquen un gol. La interacción realista con el balón y los otros jugadores, el control intuitivo y la jugabilidad futbolera te darán una experiencia inolvidable.", precio: 0}
])

const carrito = ref([])

const agregarAlCarrito = (item) => {
  let carritoItem = carrito.value.find(cartItem => cartItem.nombre === item.nombre);
  if (carritoItem) {
    carritoItem.cantidad++;
  } else {
    carritoItem = { ...item, cantidad: 1 };
    carrito.value.push(carritoItem);
  }
}

const calcularTotal = () => {
  let total = 0;
  for (const producto of carrito.value) {
    total += producto.precio * producto.cantidad;
  }
  return total;
}

function eliminarCarrito (i){
  carrito.value.splice(i,1)
}

</script>

<style scoped>

  #titulo{
    display: flex;
    justify-content: space-around;
    align-items: center;
    text-align: center;
    font-size: 125%;
    height: 80px;
    background: linear-gradient(to left, purple, rgb(0, 0, 0));
    color: white;
    position: fixed;
    width: 100%;
    z-index: 50;
  }

  #carrito{
    background-color: transparent;
    border: 0;
    cursor: pointer;
    border-radius: 50px;
    width: 80px;
    height: 50px;
  }

  #carrito:hover{
    background-color: rgb(92, 1, 92);
  }

  section{
    min-height: 100vh;
    background-color: rgb(0, 0, 0);
    font-family: 'Franklin Gothic Medium', 'Arial Narrow', Arial, sans-serif;
  }

  #busqueda{
    background-image: url('./img/fondo.jfif');
    opacity: 0.5;
    height: 500px;
    width: 100%;
    position: absolute;
    background-repeat: no-repeat;
    background-size: cover;
  }

  #conoce, #interesado{
    margin: 0; color:  white; 
    z-index: 1; 
    position: relative;
  }

  #conoce{
    font-size: 40px;
  }

  #cuadro-busqueda{
    display: grid;
    grid-template-columns: 50% 50%;
    grid-column: 3;
    height: 500px;
    align-content: center;
  }

  #masVendidos{
    display: flex;
    flex-direction: column;
    padding: 2%;
    color: white;
    align-items: center;
  }

  #masVendidos h1, h4{
    margin: 0;
  }

  .contitulos{
    width: 100%;
    background-color: rgb(39, 39, 39);
  }

  .cards{
    display: flex;
    flex-flow: row;
    flex-wrap: wrap;
    width: 100%;
    justify-content: center;
    gap: 50px;
    background-color: rgb(39, 39, 39);
    padding-bottom: 20px;
    padding-top: 20px;
  }

  .card{
    display: flex;
    height: 450px;
    width: 350px;
    background-color: rgb(24, 24, 24);
    align-items: center;
    justify-content: center;
    position: relative;
  }

  .card .face{
    position: absolute;
    width: 100%;
    height: 100%;
    backface-visibility: hidden;
    border: 10px;
    overflow: hidden;
    transition: .5s;
    display: flex;
    align-items: center;
    justify-content: center;
  }

  .card .front{
    transform: perspective(600px) rotateY(0deg);
    box-shadow: 0 5px 10px #000;
  }

  .card .front img{
    display: flex;
    position: absolute;
    width: 90%;
    height: 90%;
  }

  .card .back{
    transform: perspective(600px) rotateY(180deg);
    background: rgb(24, 24, 24);
   
    display: flex;
    flex-direction: column;
    justify-content: space-between;
  }

  .card:hover .front{
    transform: perspective(600px) rotateY(180deg);
  }

  .card:hover .back{
    transform: perspective(600px) rotateY(360deg);
  }

  .botonAgg{
    display: flex;
    gap: 20px;
    align-items: center;
    width: 100%;
    justify-content: center;
    background-color: rgb(24, 24, 24);
    border: 0;
    font-size: 15px;
    cursor: pointer;
  }

  .botonAgg:hover{
    background: linear-gradient(to left, purple, rgb(0, 0, 0));
  }

  #final{
    display: flex;
    justify-content: space-between;
    align-items: center;
    text-align: center;
    font-size: 125%;
    height: 80px;
    background: linear-gradient(to left, purple, rgb(0, 0, 0));
    color: white;
    padding-left: 25px;
    padding-right: 25px;
  }

  #final img{
    height: 45px;
  }

  .modal {
  background: rgba(0, 0, 0, 0.5);
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.5);
  display: flex;
  align-items: center;
  justify-content: center;
  z-index: 50;
}

.modal-content {
  display: flex;
  flex-direction: column;
  gap: 35px;
  width: 40%;
  max-height: 80%;
  overflow: auto;
  background-color: rgb(57, 0, 57);
  color: white;
  text-align: center;
  padding: 20px;
  border-radius: 10px;
  box-shadow: 0px 0px 10px rgba(0, 0, 0, 0.5);
}

table {
  width: 100%;
  border-collapse: collapse;
  margin-top: 10px;
}

th, td {
  padding: 10px;
  text-align: center;;
  border-bottom: 1px solid #ddd;
}

th{
  font-size: larger;
}

.imagen-producto{
  max-width: 100px;
}

#equis:hover{
  background-color: aqua;
}

</style>
