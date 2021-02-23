<template>
    <div class="game-area">
        <div>{{selected}}</div>
        <h1 class="title">Pogaça <span>Nerede </span> <strong>?</strong> </h1>
        <h4 class="description">Açık kartlardan birini sectikten sonra kapalı karta tıklayınız</h4>
        <div class="container">
            <transition-group appear name="rotate-all" class="card-container">
                <app-card
            :key="card.id"
            :class="{'shadow' : selected == card.id}"
            @click.native="selected=card.id"
            v-for="card in cards" 
            :card="card"></app-card>
            
            </transition-group>
        </div>
        <div class="container">
    
            <transition name="rotate" mode="out-in">
                <component :card="answer" :is="activeCard" @click.native="showCard(answer)">

                </component>
            
            </transition>
        </div>
    </div>
</template>

<script>
import Card from "../components/card";
import DefaultCard from "../components/defaultCard"
export default {
    components:{
        appCard : Card,
        appDefaultCard : DefaultCard
    },
    data(){
        return{
            selected:null,
            answer : {},
            activeCard : "app-default-card",
            cards:[
                {id:2, component : "app-card", image: "/src/assets/card-2.jpg"},
                {id:1, component : "app-card", image: "/src/assets/card-1.jpg"},
                {id:3, component : "app-card", image: "/src/assets/card-3.jpg"},
                {id:4, component : "app-card", image: "/src/assets/card-4.jpg"},
                {id:5, component : "app-card", image: "/src/assets/card-5.jpg"}
            ]
        }
    },
    created(){
        let answer = Math.ceil(Math.random()* this.cards.length);
        this.answer = this.cards[answer -1];
    },
    methods:{
        showCard(answer){
            
            if(this.selected == null){
                alert("ilk olarak bir kart seciniz")
            }else{
                this.activeCard = answer.component;
                setTimeout(()=>{
                    if(answer.id==this.selected){
                        this.$emit("activeComponentEvent","app-celebrate");
                    
                }else{
                    this.$emit("activeComponentEvent","app-failure");
                    
                }
                },1700)
            }

        }
    }

    
}
</script>

<style  scoped>

.title{
    text-align: center;
    color: rosybrown;
    margin-top: 70px;
}

.title span{
    color: mediumpurple;
}

.title strong{
    color: darkred;         
}

.description{
    color:grey;
    text-align: center;

}
.container, .card-container{
    display:flex; 
    justify-content: center;
    align-items: center;
    margin-top: 50px;
}
.shadow{
    box-shadow: 0px 5px 18px #30969f !important;
    transition: box-shadow .2s;
}

/*.rotate-all-enter{}*/
.rotate-all-enter-active{
    animation: rotate-all ease-in-out 1.2s forwards;
}
/*.rotate-all-leave{}
.rotate-all-leave-active{}*/

@keyframes rotate-all {
    from{
        transform: rotateY(0);
    }
    to{
        transform: rotateY(720deg);
    }
    
}

.rotate-enter-active{
    animation: rotate-in 0.5s ease-in-out forwards;
}
.rotate-leave-active{
    animation: rotate-out 0.5s ease-in-out forwards;
}

@keyframes rotate-in {
    from{
        transform: rotateY(90deg);
    }
    to{
        transform: rotateY(0deg);
    }
    
}
@keyframes rotate-out {
    from{
        transform: rotateY(0deg);
    }
    to{
        transform: rotateY(90deg);
    }
    
}






</style>>

    
