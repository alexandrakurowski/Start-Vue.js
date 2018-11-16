<template>
    <div id="departement">
        <h2> Les Départements de France</h2>
            <select v-model="selected">
                <option disabled value="">Choisissez une région</option>
                <option  v-for = "r in region" 
                        v-bind:key = "r.id"
                    
                        >{{r.nom}}</option> 
        </select>
        <span>Sélectionné : {{ selected }}</span> 
        <!-- le span permet d'afficher en ligne -->

        <!-- <ul>
        <li v-for = "r in departement" v-bind:key= "r.id">{{r.nom}}</li>
     </ul> -->
    </div>
</template>

<script>
    import $ from 'jquery'; 
    


    export default {
        name: 'departement',
        data () {
            return {
                departement:[]
            }
        },
        created: function()
        {
            $.ajax('https://geo.api.gouv.fr/departements')
            .done (function(d){
                this.departement= d;
            }.bind(this));

        }
        
    }

</script>



