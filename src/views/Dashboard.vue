<template>
    <div class="dashboard">
        <Header/>
    <div class="container">
        <table class="table table-hover">
            <thead>
                <tr>
                <th scope="col">ID</th>
                <th scope="col">Name</th>
                <th scope="col">Dni</th>
                <th scope="col">Phone</th>
                <th scope="col">Email</th>

                </tr>
            </thead>
            <tbody>
                <tr v-for="pacient of listPacient" :key="pacient.PacienteId">
                <th scope="row">{{pacient.PacienteId}}</th>
                <td>{{pacient.Nombre}}</td>
                <td>{{pacient.DNI}}</td>
                <td>{{pacient.Telefono}}</td>
                <td>{{pacient.Correo}}</td>
               <button class="btn btn-warning sm" v-on:click="editar(pacient.PacienteId)">Modificar</button> 
                </tr>
                
            </tbody>
        </table>
    </div>
        <Footer/>
        
    </div>
</template>
<script>
import Header from '@/components/Header.vue'
import Footer from '@/components/Footer.vue'
import axios from 'axios'

export default {
    name:"Dashboard",
    data(){
        return{
            listPacient:null,
            page:1
        }
    },
    components:{
        Header,
        Footer
    },
    methods:{
        editar(id){
            this.$router.push('/editar/'+id);
        }
    },
    mounted(){
        let api ="https://api.solodata.es/pacientes?page=" + this.pagina;
        axios.get(api).then( data =>{
            this.listPacient = data.data;
        })
    }
}
</script>
<style scope>

</style>