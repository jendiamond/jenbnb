<template>
<div>
    <div style="display: flex">
        <img v-for="image in home.images" :key="image" :src="image" width="200"/>
    </div>
    {{ home.title }}<br>
    ${{ home.pricePerNight }} / night<br>
    <img src="/images/marker.svg" alt="map-marker" width="20">{{ home.location.address }}
    {{ home.location.city }}
    {{ home.location.state }}
    {{ home.location.country }}<br>
    <img src="/images/star.svg" alt="star" width="20">{{ home.reviewValue }}<br>
    {{ home.guests }} guests,
    {{ home.bedrooms }} rooms,
    {{ home.beds }} beds,
    {{ home.bathrooms }} bath
    </div>
</template>

<script>
import homes from '~/data/homes'

export default {
    head(){
        return {
            title: this.home.title
        }
    },
    data(){
        return {
            home: {}
        }
    },
    created() {
        const home = homes.find((home) =>home.objectID == this.$route.params.id)
        this.home = home
    },
}
</script>
