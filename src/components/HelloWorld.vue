<template>
    <div style="display: flex">
        <div class="left-panel">
            <div v-for="list in lists" :key="list.id" class="list">
                <div class="list-header" @click="toggleListCollapse(list)">
                    <span>{{ list.name }}</span>
                    <button>{{ list.collapsed ? 'Развернуть' : 'Свернуть' }}</button>
                </div>
                <div v-if="!list.collapsed">
                    <input type="checkbox" v-model="list.selectAll" @change="toggleSelectAll(list)">
                    <span>Выбрать все</span>
                    <div v-for="item in list.items" :key="item.id" class="item">
                        <input type="checkbox" v-model="item.selected">
                        <input type="number" v-model.number="item.quantity" min="0">
                        <input type="color" v-model="item.color">
                    </div>
                </div>
            </div>
        </div>
        <div class="right-panel">
            <div v-for="list in sortedLists" :key="list.id" class="list">
                <h3>{{ list.name }}</h3>
                <div v-for="item in list.items" :key="item.id" class="item">
                    <div v-for="n in item.quantity" :key="n" class="square" :style="{ backgroundColor: item.color }"></div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>

export default {
    name: 'ItemList',
    data() {
        return {
            lists: [
                {
                    id: 1,
                    name: 'List 1',
                    selectAll: false,
                    collapsed: false,
                    items: [
                        { id: 1, quantity: 2, color: '#ff0000', selected: false },
                        { id: 2, quantity: 3, color: '#00ff00', selected: false },
                        { id: 3, quantity: 1, color: '#0000ff', selected: false },
                    ]
                },
                {
                    id: 2,
                    name: 'List 2',
                    selectAll: false,
                    collapsed: false,
                    items: [
                        { id: 1, quantity: 2, color: '#ff0000', selected: false },
                        { id: 2, quantity: 3, color: '#00ff00', selected: false },
                        { id: 3, quantity: 1, color: '#0000ff', selected: false },
                    ]
                },
                {
                    id: 3,
                    name: 'List 3',
                    selectAll: false,
                    collapsed: false,
                    items: [
                        { id: 1, quantity: 2, color: '#ff0000', selected: false },
                        { id: 2, quantity: 3, color: '#00ff00', selected: false },
                        { id: 3, quantity: 1, color: '#0000ff', selected: false },
                    ]
                },
            ]
        };
    },
    methods: {
        toggleSelectAll(list) {
            const allSelected = list.items.every(item => item.selected);
            list.items.forEach(item => {
                item.selected = !allSelected;
            });
        },
        sortList(list) {
            list.items.sort((a, b) => a.id - b.id);
        },
        shuffleList(list) {
            for (let i = list.items.length - 1; i > 0; i--) {
                const j = Math.floor(Math.random() * (i + 1));
                [list.items[i], list.items[j]] = [list.items[j], list.items[i]];
            }
        },
        toggleListCollapse(list) {
            list.collapsed = !list.collapsed;
        },
    },
    computed: {
        sortedLists() {
            return this.lists.map(list => {
                const sortedList = { ...list };
                if (sortedList.sorted) {
                    this.sortList(sortedList);
                } else {
                    this.shuffleList(sortedList);
                }
                return sortedList;
            });
        },
    },
};
</script>

<style>
.list {
    margin-bottom: 10px;
}
.item {
    display: flex;
    align-items: center;
    margin-bottom: 5px;
}
.square {
    width: 20px;
    height: 20px;
    margin-right: 5px;
}
.left-panel{
    width: 50%;
}
.right-panel{
    width: 50%;
}
</style>