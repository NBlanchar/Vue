<template>    
    <div class="container">
        <h1>{{titulo}}</h1>
        <div class="row">
            <div class="col-md-6">
            <label>Nombre</label>
            <input type="text" class="form-control" v-model="nombre">
            <label>Nota</label>
            <input type="number" class="form-control" v-model="nota">
            <button class ="btn btn-success" v-on:click="agregarNota">agregar</button>
        </div>
        <div class="col-md-6">
            <table class="table">
                <thead>
                    <tr>
                        <th>ID</th>
                        <th>Nombre</th>
                        <th>Nota</th>
                    </tr>
                </thead> 
                <tbody>
                    <tr v-for="user in usuarios" :key="user.id" v-bind:style="user.estado==false?'color:red':''">
                        <td v-text="user.id"></td>
                        <td v-html="user.name"></td>
                        <td v-text="user.nota"></td>
                    </tr> 
                </tbody>
            </table>
        </div>
        </div>
    </div>      
</template>

<script>
    export default {
        data(){
            return{
                titulo: 'Lista de Calificaciones',
                usuarios:[
                        {id:1,name:'c1',nota:3.2, estado:true},
                        {id:2,name:'<h1>carlos</h1>',nota:2.5, estado:false},
                        {id:3,name:'c3',nota:4.6, estado:true},
                        {id:4,name:'c4',nota:6, estado:true}
                ],
                nombre: '',
                nota:0,
                count:5
            }
        },
        methods:{
            agregarNota: function(){
                let NEstado= false;
                if(this.nota>=3){
                    NEstado=true;
                }
                if(this.nombre!="" && this.nota!=""){
                    
                    this.usuarios.push({id:this.count,name:this.nombre,nota:this.nota,estado:NEstado})
                    this.count++
                    this.nombre="";
                    this.nota="";

                }else{                    
                    alert("Complete correctamente los campos");   
                }            
            }

        }
    }  
</script>

<style>

</style>