<template>
    <div class="list">
        <div class="list-header">
            <h3>{{ list.name }}</h3>
            <button @click="this.isSorted = !this.isSorted">{{this.isSorted ? 'Перемешать' : 'Отсортировать'}}</button>
        </div>
        <div v-for="groups in shuffledSquaresList" :key="groups[0]" class="group">
            <div
                v-for="(square, index) in groups"
                :key="index"
                class="square"
                :style="{ backgroundColor: square }"
                @click="decreaseQuantity(square)"
            />
        </div>
    </div>
</template>

<script>

export default {
    props:{
        list: {
            type: Object,
            required: true
        }
    },
    data(){
        return{
            isSorted: false,
        }
    },
    methods:{
        decreaseQuantity(square) {
            const item = this.list.items.find(item => item.color === square);
            if (item.quantity > 0){
                item.quantity--
            }
        }
    },
    computed: {
        squaresList(){
            const squaresColor = []

            this.list.items.map((item) => {
                const groupByColor = [];
                if(item.selected){
                    for (let i = 0; i < item.quantity; i++){
                        groupByColor.push(item.color)
                    }
                }
                squaresColor.push(groupByColor)
            })
            return squaresColor
        },

        shuffledSquaresList(){
          if (this.isSorted) {
              return this.squaresList
          }
          let connectedToSingleAndShuffled = [];
          this.squaresList.forEach(clrs=>{
              connectedToSingleAndShuffled = [...connectedToSingleAndShuffled, ...clrs]
          })
          return [connectedToSingleAndShuffled.sort(()=> Math.random() - 0.5)]
        }
    }
}
</script>

<style scoped>
.list{
    border: 1px solid #000;
    padding: 10px 15px;
    margin-bottom: 10px;
}
.list-header{
    display: flex;
    justify-content: space-between;
}
.list-header button{
    color: white;
    background-color: #5867ff;
    border: none;
    padding: 5px;
    border-radius: 10px;
    cursor: pointer;
}
.group{
    display: flex;
    flex-wrap: wrap;
}
.square {
    width: 15px;
    height: 15px;
    margin: 1px;
    cursor: pointer;
}
</style>