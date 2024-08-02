<script>
import { store } from '../store.js';
export default {
    data() {
        return {
            store,
        }
    },
    methods: {
       
    },
}
</script>
<template>
    <div>
        <select class="form-select mt-3" name="archetype" id="" @change="$emit('filter_cards')" v-model="store.archetype_search">
            <option value="">Seleiona Archetipo</option>
            <option :value="archetype.archetype_name" v-for="archetype, index in store.archetypeList">{{ archetype.archetype_name }}</option>
        </select>
    </div>
</template>
<style lang="scss" scoped>
    
</style>