<template>
<div id="region">
    <h2> Les régions de France</h2>
    <select v-model="selected">
        <option disabled value="">Choisissez une région</option>
        <option  v-for = "r in region" 
                v-bind:key = "r.id"
                v-bind:value = "r.code"               
                >{{r.nom}}</option> 
    </select>
    <span>Sélectionné : {{ selected }}</span> 
     <!-- le span permet d'afficher en ligne -->

    <!-- <ul>
        <li v-for = "r in region" v-bind:key= "r.id">{{r.nom}}</li>
     </ul> -->
</div>
</template>

<script>
    import $ from 'jquery'; 
    


    export default {
        name: 'region',
        data () {
            return {
                region:[],
                selected:""
            }
        },
        created: function(){
            $.ajax('https://geo.api.gouv.fr/regions')
            .done (function(d){

                this.region = d;
            }.bind(this));
        }   
    }

</script>

