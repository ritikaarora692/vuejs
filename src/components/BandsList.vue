<template>
<div>
<input type="text" placeholder="Add Band"  @click.stop v-model="newBand">
<button @click="addBand()"> Add </button>
    <ul>
        <BandItem v-for="band in bands" :key="band.id" :band=band>
            {{band.name}}
        </BandItem>
    </ul>
    </div>
</template>
<script>
import BandItem from './BandItem.vue'
export default{
    name: 'BandList',
    components: {
    BandItem
  },
    data(){
        return{
            newBand: '',
            bands:[{
                id: 1,
                name: 'ColdPlay',
                songs: ['Hymn For the Weekend', 'Paradise']
            },{
                id: 2,
                name: 'Chainsmoker',
                songs: ['closer', 'Something just like this']
            }]
        }
    },
    methods:{
        addBand(){
            this.bands.push({
                id: Math.floor((Math.random()*100)+1),
                name: this.newBand,
                songs: []
            })
            this.newBand = ''
        }
    }
}
</script>
