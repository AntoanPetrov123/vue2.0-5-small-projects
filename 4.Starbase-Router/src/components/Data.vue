<template>
    <div class="col-md-12 items">
        <app-item v-for="(item, index) in items" :key="index" :passed-item="item" :type="type"></app-item>
    </div>
</template>

<script>
import Item from './Item.vue';

export default {
    data() {
        return {
            type: this.$route.params.type,
            items: []
        };
    },
    watch: {
        '$route': 'fetchItems'
    },
    //watch for changing queries in link
    methods: {
        fetchItems() {
            this.items = [];
            this.type = this.$route.params.type;
            let initial_ids = [1, 13, 14];

            for (let i in initial_ids) {
                let id = initial_ids[i];
                fetch(`http://swapi.dev/api/${this.type}/${id}`, {
                    method: 'GET'
                })
                    .then(res => {
                        return res.json();
                    })
                    .then(data => {
                        this.items.push(data);
                    })
            }
        }
    },
    components: {
        appItem: Item
    },
    created() {
        this.fetchItems();
    }
};
</script>