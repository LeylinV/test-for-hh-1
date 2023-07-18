<template>
    <div class="lists-page">
        <div class="panel">
            <lists-with-check
                :lists="lists"
                @toggleListCollapse="toggleListCollapse"
            />
        </div>
        <div class="panel">
            <list-with-squares
                v-for="list in lists"
                :list="list"
                :key="list.id"
            />
        </div>
    </div>
</template>

<script>
import ListsWithCheck from "@/components/ListsWithCheck/ListsWithCheck";
import ListWithSquares from "@/components/ListWithSquares/ListWithSquares";

export default {
    components:{
        ListsWithCheck,ListWithSquares
    },
    data() {
        return {
            lists: [
                {
                    id: 1,
                    name: 'List 1',
                    selectAll: false,
                    isIndeterminate: false,
                    collapsed: false,
                    items: [
                        { id: 1, name: 'Item 1', quantity: 21, color: '#FF0000', selected: true },
                        { id: 2, name: 'Item 2', quantity: 35, color: '#00FF00', selected: true },
                        { id: 3, name: 'Item 3', quantity: 12, color: '#0000FF', selected: true },
                        { id: 4, name: 'Item 4', quantity: 8, color: '#FFFF00', selected: false },
                        { id: 5, name: 'Item 5', quantity: 9, color: '#FF00FF', selected: false },
                        { id: 6, name: 'Item 6', quantity: 15, color: '#00FFFF', selected: false },
                        { id: 7, name: 'Item 7', quantity: 17, color: '#FFA500', selected: false },
                    ]
                },
                {
                    id: 2,
                    name: 'List 2',
                    selectAll: false,
                    isIndeterminate: false,
                    collapsed: false,
                    items: [
                        { id: 1, name: 'Item 1', quantity: 21, color: '#FF0000', selected: false },
                        { id: 2, name: 'Item 2', quantity: 35, color: '#00FF00', selected: false },
                        { id: 3, name: 'Item 3', quantity: 12, color: '#0000FF', selected: false },
                        { id: 4, name: 'Item 4', quantity: 8, color: '#FFFF00', selected: false },
                    ]
                },
                {
                    id: 3,
                    name: 'List 3',
                    selectAll: false,
                    isIndeterminate: false,
                    collapsed: false,
                    items: [
                        { id: 1, name: 'Item 1', quantity: 21, color: '#FF0000', selected: false },
                        { id: 2, name: 'Item 2', quantity: 35, color: '#00FF00', selected: false },
                        { id: 3, name: 'Item 3', quantity: 12, color: '#0000FF', selected: false },
                        { id: 4, name: 'Item 4', quantity: 8, color: '#FFFF00', selected: false },
                    ]
                },
                {
                    id: 4,
                    name: 'List 4',
                    selectAll: false,
                    isIndeterminate: false,
                    collapsed: false,
                    items: [
                        { id: 1, name: 'Item 1', quantity: 21, color: '#FF0000', selected: false },
                        { id: 2, name: 'Item 2', quantity: 35, color: '#00FF00', selected: false },
                        { id: 3, name: 'Item 3', quantity: 12, color: '#0000FF', selected: false },
                        { id: 4, name: 'Item 4', quantity: 8, color: '#FFFF00', selected: false },
                    ]
                },
                {
                    id: 5,
                    name: 'List 5',
                    selectAll: false,
                    isIndeterminate: false,
                    collapsed: false,
                    items: [
                        { id: 1, name: 'Item 1', quantity: 21, color: '#FF0000', selected: false },
                        { id: 2, name: 'Item 2', quantity: 35, color: '#00FF00', selected: false },
                        { id: 3, name: 'Item 3', quantity: 12, color: '#0000FF', selected: false },
                        { id: 4, name: 'Item 4', quantity: 8, color: '#FFFF00', selected: false },
                    ]
                },
            ]
        };
    },
    methods: {
        toggleListCollapse(list) {
            list.collapsed = !list.collapsed;
        },
    },
    computed: {

    },
};
</script>

<style>
.lists-page{
    display: flex;
    justify-content: space-between;
    min-height: 100vh;
    padding: 30px;
}
.panel{
    width: 45%;
    border: 1px solid #000;
    padding: 40px 30px
}

</style>