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
                        { id: 1, name: 'Item 1', quantity: 2, color: '#ff0000', selected: false },
                        { id: 2, name: 'Item 2', quantity: 3, color: '#00ff00', selected: false },
                        { id: 3, name: 'Item 3', quantity: 1, color: '#0000ff', selected: false },
                        { id: 4, name: 'Item 4', quantity: 5, color: '#ff23e2', selected: false },
                    ]
                },
                {
                    id: 2,
                    name: 'List 2',
                    selectAll: false,
                    isIndeterminate: false,
                    collapsed: false,
                    items: [
                        { id: 1, name: 'Item 1', quantity: 2, color: '#ff0000', selected: false },
                        { id: 2, name: 'Item 2', quantity: 3, color: '#00ff00', selected: false },
                        { id: 3, name: 'Item 3', quantity: 1, color: '#0000ff', selected: false },
                    ]
                },
                {
                    id: 3,
                    name: 'List 3',
                    selectAll: false,
                    isIndeterminate: false,
                    collapsed: false,
                    items: [
                        { id: 1, name: 'Item 1', quantity: 2, color: '#ff0000', selected: false },
                        { id: 2, name: 'Item 2', quantity: 3, color: '#00ff00', selected: false },
                        { id: 3, name: 'Item 3', quantity: 1, color: '#0000ff', selected: false },
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