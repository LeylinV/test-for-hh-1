<template>
    <div v-for="item in list.items" :key="item.id" class="item">
        <div>
            <input
                class="checkbox"
                type="checkbox"
                v-model="item.selected"
                @change="toggleItemSelection(item)"
            >
            <span>{{item.name}}</span>
        </div>
        <div>
            <input class="number" type="number" v-model.number="item.quantity" min="0">
            <input class="color" type="color" v-model="item.color">
        </div>
    </div>
</template>

<script>
export default {
    props:{
        list: {
            type: Object,
            required: true
        },
    },
    data(){
        return{}
    },
    methods: {
        toggleItemSelection(item) {
            this.$emit("toggleItemSelection", item);
        }
    },
    emits: ['toggleItemSelection'],
}
</script>

<style scoped>
.item {
    width: 75%;
    display: flex;
    align-items: center;
    justify-content: space-between;
    margin: 0 0 5px 50px
}
.item div {
    display: flex;
    align-items: center;
}
.checkbox{
    margin-right: 10px;
}
.number{
    padding: 2px;
    width: 40px;
}
.color{
    width: 30px;
}
</style>