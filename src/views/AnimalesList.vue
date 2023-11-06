<template>
    <h1>Lista de animales</h1>
    <div id="card">
        <h3>Nuevo animal</h3>
        <input type="text" placeholder="Escribe un animal" v-model="nuevoAnimal">
        <br>
        <button id="btnAdd">Agregar</button>
    </div>
    <br>
    <div id="card">
        <h4>Animales</h4>
        <!-- Se recorren los animales almacenados en el arreglo -->
        <p v-for="(animal, i) in animales" :key="i">{{ animal }} </p>
    </div>
</template>

<script>
    export default {
    name: 'AnimalesList',
    data(){
        return {
            // Esta variable guardará todos los animales
            animales: [],
            // Esta variable guardará el animal ingresado en el input
            nuevoAnimal: ''
        }
    },
    methods: {
        // Este método insertará el nuevo animal en el arreglo
        agregarAnimal(){
            this.animales.push(this.nuevoAnimal)
            this.nuevoAnimal = ''
        }
    },
        beforeCreate(){
        alert('Inicia la creación del componente')
    },
    created(){
        console.log('Componente creado')
            // Se agregan dos animales al arreglo
            let guardados = ['Jirafa','León']
            guardados.forEach(element => {
            this.animales.push(element)
        });
    },
    beforeMount(){
        alert('El componente está cerca de renderizar')
    },
    mounted(){
        console.log('El componente se ha renderizado')
            // Se agrega el evento clic al botón
            let btnAdd = document.getElementById('btnAdd')
            btnAdd.addEventListener('click', this.agregarAnimal)
    },
    beforeUpdate(){
        alert('El componente ha sufrido un cambio en las propiedades o estado')
    },
    updated(){
        console.log('El componente se ha actualizado y el DOM ha sido modificado')
    },
    beforeUnmount() {
        alert('El componente iniciará a desmontarse')
    },
    unmounted() {
        console.log('El componente ha sido desmontado')
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
    width: 180px;
    padding: 10px;
    margin: 20px;
    background-color: yellowgreen;
    border-radius: 40px;
    color: black;
    }
</style>
    