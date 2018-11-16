<template>
    <div id="departement">
        <h2> Les Départements de France</h2>
            <select v-model="selected"
                    v-on:change = "villelist">>
                <option disabled value="">Choisissez un département</option>
                <option  v-for = "r in departement" 
                        v-bind:key = "r.id"
                        v-bind:value = "r.code"
                    
                        >{{r.nom}}</option> 
        </select>
        <span>code département sélectionné : {{ selected }}</span> 
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
                departement:[],
                selected:""
            }
        },
        methods:{
            villelist: function(e){
                    
                console.log(e.target.value);
                this.$root.$emit("depselect",e.target.value)
                console.log(this);
                    
             }
            },
        // created: function()
        // {
        //     $.ajax('https://geo.api.gouv.fr/departements')
        //     .done (function(d){
        //         this.departement= d;
        //     }.bind(this));
        // },
// mounted remplace created lorsqu on ecoute message d'une autre vue et associe des fonctions pour ecrire donnees
        mounted: function() 
        {
            this.$root.$on("regionselect", data=>
           
            {
                console.log(data);
                $.ajax('https://geo.api.gouv.fr/regions/'+ data +'/departements')
                .done (function(d){
                    this.departement= d;
                }.bind(this));
            });
        }
        
    }

</script>



