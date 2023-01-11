<template>
    <div id="contenedor">
        <h1>{{ pantalla }}</h1>

        <div class="teclas">
            <div class="numeros">
                <Btn texto="1" @click="sagregarPantalla(1)"></Btn>
                <Btn texto="2" @click="agregarPantalla(2)"></Btn>
                <Btn texto="3" @click="agregarPantalla(3)"></Btn>
                <Btn texto="4" @click="agregarPantalla(4)"></Btn>
                <Btn texto="5" @click="agregarPantalla(5)"></Btn>
                <Btn texto="6" @click="agregarPantalla(6)"></Btn>
                <Btn texto="7" @click="agregarPantalla(7)"></Btn>
                <Btn texto="8" @click="agregarPantalla(8)"></Btn>
                <Btn texto="9" @click="agregarPantalla(9)"></Btn>
                <Btn texto="0" @click="agregarPantalla(0)"></Btn>
                <Btn texto="=" @click="calcularResultado"></Btn>
            </div>

            <div class="operaciones">
                <Btn texto="+" @click="agregarSuma()"></Btn>
                <Btn texto="-" @click="agregarResta()"></Btn>
                <Btn texto="/" @click="agregarDiv()"></Btn>
                <Btn texto="*" @click="agregarMulti()"></Btn>
            </div>
        </div>
    </div>


</template>

<script>
import Btn from './Btn.vue'

export default {
    components: {
        Btn
    },
    data() {
        return {
            pantalla: "0",
            resultado: null
        }
    },
    props: {
        textoPantalla: {
            type: Number,
            default: 0
        }
    },
    methods: {
        agregarPantalla(num) {
            console.log(this.pantalla)
            if (this.pantalla != "0") {
                this.pantalla = this.pantalla.concat(num)
            } else {
                this.pantalla = num.toString()
            }

        }
        ,
        agregarSuma() {
            this.pantalla = this.pantalla.concat("+")
        }
        , agregarResta() {
            this.pantalla = this.pantalla.concat("-")
        }
        ,
        agregarMulti() {
            this.pantalla = this.pantalla.concat("*")
        }
        ,
        agregarDiv() {
            this.pantalla = this.pantalla.concat("/")
        }
        ,
        calcularResultado() {
            if (this.pantalla.includes('+')) {
                let arr = this.pantalla.split('+')
                this.pantalla = (parseInt(arr[0]) + parseInt(arr[1])).toString()
            } else {
                if (this.pantalla.includes('-')) {
                    let arr = this.pantalla.split('-')
                    this.pantalla = (parseInt(arr[0]) - parseInt(arr[1])).toString()
                } else {
                    if (this.pantalla.includes('/')) {
                        let arr = this.pantalla.split('/')
                        this.pantalla = (parseInt(arr[0]) / parseInt(arr[1])).toString()
                    } else {
                        if (this.pantalla.includes('*')) {
                            let arr = this.pantalla.split('*')
                            this.pantalla = (parseInt(arr[0]) * parseInt(arr[1])).toString()
                        } 
                    }
                }
            }
        }

    }
}
</script>

<style>
h1 {

    height: 40px;
    background-color: white;
    border-radius: 5px;
    border: 2px solid black;
    text-align: right;
    padding: 2px 15px;
}

#contenedor {
    display: grid;
    background-color: #2196F3;
    border-radius: px;
    padding: 10px;
    height: 600px;
    width: 300;
}

button {
    padding: 2px 15px;
    border-radius: 5px;
    margin: 10px 15px;
    font-size: 50px;

}

.numeros {
    display: grid;
    height: 400px;
    align-content: space-evenly;
    grid-template-columns: auto auto auto;

    padding: 10px;
}

.teclas {
    display: grid;
    align-content: space-evenly;
    grid-template-columns: auto auto;
    padding: 10px;
}

.operaciones {
    display: grid;
    align-content: space-evenly;
    grid-template-columns: auto;
    padding: 10px;
}
</style>