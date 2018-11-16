<template>
    <div id="commune">

        <h2>les communes</h2>
            <select v-model="selected">
                <option disabled value="">Choisissez une commune</option>
                <option  v-for = "c in commune " 
                        v-bind:key = "c.id"
                        v-bind:value = "c.code"
                    
                        >{{c.nom}}</option> 
        </select>
        <span>Code Postal : {{ selected }}</span> 
    </div>
</template>

<script>
    import $ from 'jquery'; 
    


    export default {
        name: 'commune',
        data () {
            return {
                commune:[],
                selected:""
            }
        },
        mounted: function()
        {   this.$root.$on("depselect", data=>
            {
            $.ajax('https://geo.api.gouv.fr/departements/' + data + '/communes')
            .done (function(d){
                this.commune= d;
            }.bind(this));
console.log(commune);
            })
        },
        
    }

</script>

