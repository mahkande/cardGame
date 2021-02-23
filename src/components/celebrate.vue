<template>
   <div class="container">
       <h1>Tebrikler Bildiniz :)) </h1>
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
    position: absolute;
    top: 0px;
    left: 0px;
    width: 100%;
    height: 100%;
    margin-top: 100px;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
}
.container h1{
    text-align: center;
    font-size: 333%;
    color:darkgreen;
    font-weight: bold;
    opacity: .5;

}

.container button{
    width:200px;
    background:#fff;
    color: rgb(85, 5, 5);
    border: 1px solid darkred;
    height: 50px;
    font-size: 20px;
    border-radius: 5px;
    outline: none;
    cursor: pointer;
    transition: all 0.5s;
    margin-top: 50px;
    
}

.container button:hover{
    border: 2px solid rgb(52, 236, 15);
    background:rgb(126, 221, 122);
    color:white;
    transition: all 0.5s;
}


</style>>


    
