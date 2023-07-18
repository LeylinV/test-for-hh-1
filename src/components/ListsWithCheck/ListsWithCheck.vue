<template>
    <div v-for="list in lists" :key="list.id" class="list">
        <div class="list-header">
            <div class="list-arrow" @click="toggleListCollapse(list)">
                <i  class="bottom" :class="{'closed' : list.collapsed}"></i>
            </div>
            <input type="checkbox" v-model="list.selectAll" :indeterminate="list.isIndeterminate" @change="toggleSelectAll(list)" />
            <span>{{ list.name }}</span>
        </div>
        <div v-if="!list.collapsed">
            <ItemsList :list="list" @toggleItemSelection="updateListSelection(list)"/>
        </div>
    </div>
</template>

<script>
import ItemsList from "@/components/ListsWithCheck/ItemsList/ItemsList";
export default {
    components: {
        ItemsList
    },
    props:{
        lists:{
            type: Array,
            required:true
        }
    },
    data(){
        return{}
    },
    methods: {
        toggleListCollapse(list){
            this.$emit('toggleListCollapse', list);
        },
        toggleSelectAll(list) {
            const allSelected = list.items.every(item => item.selected);
            list.items.forEach(item => {
                item.selected = !allSelected;
            });
            this.updateListSelection(list);
        },
        updateListSelection(list) {
            const allSelected = list.items.every(item => item.selected);
            const noneSelected = list.items.every(item => !item.selected);

            if (allSelected) {
                list.selectAll = true;
                list.isIndeterminate = false;
            } else if (noneSelected) {
                list.selectAll = false;
                list.isIndeterminate = false;
            } else {
                list.selectAll = false;
                list.isIndeterminate = true;
            }
        }
    },
    emits: ['toggleListCollapse'],
}
</script>

<style scoped>
.list {
    margin-bottom: 10px;
}
.list-header{
    display: flex;
}
.list-header span{
    padding-left: 10px;
}

.list-arrow{
    padding-right: 15px;
}
i {
    cursor: pointer;
    border: solid black;
    border-width: 0 1px 1px 0;
    display: inline-block;
    padding: 5px;
    font-size: 20px
}
.bottom {
    transform: rotate(45deg);
    -webkit-transform: rotate(45deg);
}
.closed{
    transform: rotate(-45deg);
    -webkit-transform: rotate(-45deg);
}

</style>