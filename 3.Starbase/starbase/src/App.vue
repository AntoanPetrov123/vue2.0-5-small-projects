<template>
    <div id="app">
        <h3>{{ title }}</h3>
        <div class="col-md-12 team">
            <app-character v-for="(id, index) in initials_ids" :id="id" :key="index"></app-character>
        </div>
    </div>
</template>

<script>
import Character from './components/Character.vue';

export default {
    name: 'app',
    data() {
        return {
            title: 'Generate Your Team',
            initials_ids: [1, 13, 14]
        }
    },
    components: {
        appCharacter: Character
    },
    methods: {

    }
}
</script>
