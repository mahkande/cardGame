<template>
   <div class="container">
       <h1>Maalesef Bilemediniz :( </h1>
       <button @click="newGame">Yeni Oyun</button>
   </div>
</template>

<script>
export default {
    methods:{
        newGame(){
            this.$emit("activeComponentEvent","app-game-cards");

        }
    }
    
}
</script>

<style scoped>

.container{
    width: 100vw;
    height: 100vh;
    background:chocolate;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
}
.container h1{
    text-align: center;
    font-size: 333%;
    color:wheat;
    font-weight: bold;
}

.container button{
    width:200px;
    background:#fff;
    color: darkred;
    border: 1px solid white;
    height: 50px;
    font-size: 20px;
    border-radius: 5px;
    outline: none;
    cursor: pointer;
    transition: all 0.5s;
    margin-top: 40px;
    
}

.container button:hover{
    border: 2px solid darkred;
    background:rgb(168, 75, 75);
    color:white;
    transition: all 0.5s;
}


</style>>


    
