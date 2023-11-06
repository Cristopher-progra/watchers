<template>
    <h1>Calculadora</h1>
    <div id="card">
        <table>
            <tr>
                <td>Operación</td>
                <td>
                    <select v-model="operacion">
                    <option v-for="(op,i) in operaciones" :key="i" :value="op.id">
                      {{op.nombre}}
                    </option>
                    </select>
                </td>
            </tr>
            <tr>
                <td>Número 1</td>
                <td><input type="number"  v-model="numero1"></td>
            </tr>
            <tr>
                <td>Número 2</td>
                <td><input type="number"  v-model="numero2"></td>
            </tr>
            <tr>
                <td colspan="2">
                    <hr>
                    <button n @click="calcular">Calcular</button>
                </td>
            </tr>
        </table>
    </div>
    <br>
    <div id="card">
        <h4>Respuesta:  {{ resultado }} </h4>
    </div>
</template>

<script>
export default {
    name: 'CalculadoraView',
    data(){
        return {
            // Esta variable guarda las opciones del select
            operaciones: [],
            // Esta variable guarda la respuesta
            resultado: 0,
            // Esta variable guarda la opción del select seleccionada
            operacion: 1,
            // Estas variables guardan los números ingresados en los inputs
            numero1 : 0,
            numero2 : 0
        }
    },
    methods: {
    // Este método calcula la respuesta
    calcular(){
            if(this.operacion==1){
                this.resultado = this.numero1+this.numero2
            } else if(this.operacion==2){
                this.resultado = this.numero1-this.numero2
            }
        }
    },
    mounted(){
        // Se agregan las operaciones al arreglo
        // cuando el componente se ha renderizado
        this.operaciones.push({id: 1, nombre: 'Suma'})
        this.operaciones.push({id: 2, nombre: 'Resta'})
    },
    watch: {
        // Se ejecuta cuando se cambia la opción del select
    operacion(nuevoValor, antiguoValor){
        if(nuevoValor!==antiguoValor){
            this.calcular()
            }
        },
    // Se ejecuta cuando se cambia el valor del input número 1
    numero1(nuevoValor, antiguoValor){
        if(nuevoValor!==antiguoValor){
            this.calcular()
            }
        },
    // Se ejecuta cuando se cambia el valor del input número 2
    numero2(nuevoValor, antiguoValor){
        if(nuevoValor!==antiguoValor){
            this.calcular()
            }
        }
    }
}
</script>

<style scoped>
    #card {
    border: 1px solid yellowgreen;
    border-radius: 40px;
    margin: auto;
    width: 50%;
    padding: 20px;
    }
    button{
    border: 1px solid darkolivegreen;
    width: 100%;
    padding: 10px;
    background-color: yellowgreen;
    color: black;
    }
    table {
    margin: auto;
    }
    select {
    width: 100%;
    }
</style>
    