<template>
    <div class='user-card'>
        <p>name: {{this.user.name}}</p>
        <p>e-mail: {{this.user.email}}</p>
        <p>city: {{this.user.address.city}}</p>
        <p>street: {{this.user.address.street}}</p>
        <a :href="'geo:'+this.user.address.geo.lat+','+this.user.address.geo.lng">Show on map</a>
    </div>
</template>

<script lang="ts">
import Vue from "vue";
import {IUserProps} from '@/types'

export default Vue.extend<null,null,null,IUserProps>({
    props:{
        user: Object
    }
});
</script>

<style>
.user-card{
    border: 1rem solid #374;
}
</style>