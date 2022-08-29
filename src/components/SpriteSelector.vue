<template>
    <div  v-bind:class='name'></div>
</template>

    <script>
        export default {
            name: 'SpriteSelector',
            data() {
                return {
                }
            },
            props: {
                name:String,
            }
        }
    </script>

 <style scoped>
        
        .idle{
             background-size:100% 100%;
             height:100%;
             width:100%;
        }

        .animation{
             background-size:100% 100%;
             height:80%;
             width:30%;
             align-self: end;
        }



        .phoenix {
            background-image: url(../assets/PhoenixIdle.webp);
        }

        .phoenix0 {
            background-image: url(../assets/PhoenixIdle.webp);
        }

        .phoenix1 {
             background-image: url(../assets/PhoenixTurn.gif);
        }

        .phoenix2 {
             background-image: url(../assets/PhoenixTurn2.webp);
        }

        .phoenix3 {
             background-image: url(../assets/PhoenixLose.webp);
        }

        .phoenix4 {
             background-image: url(../assets/PhoenixWin.webp);
        }
        
        .mia {
            background-image: url(../assets/MiaIdle.webp);
        }

        .mia0 {
            background-image: url(../assets/MiaIdle.webp);
        }
        
        .mia1 {
            background-image: url(../assets/MiaTurn.gif);
        }
        
        .mia2 {
            background-image: url(../assets/MiaTurn2.webp);
        }
        
        .mia3 {
            background-image: url(../assets/MiaLose.gif);
        }

        .mia4 {
            background-image: url(../assets/MiaWin.gif);
        }

        .apollo {
            background-image: url(../assets/ApolloIdle.gif);
        }

        .apollo0 {
            background-image: url(../assets/ApolloIdle.gif);
        }

        .apollo1 {
            background-image: url(../assets/ApolloTurn.webp);
        }

        .apollo2 {
            background-image: url(../assets/ApolloTurn2.webp);
        }

        .apollo3 {
            background-image: url(../assets/ApolloLose.gif);
        }

        .apollo4 {
            background-image: url(../assets/ApolloWin.gif);
        }
        
        .gregory {
            background-image: url(../assets/GregoryIdle.gif);
        }

        .gregory0 {
            background-image: url(../assets/GregoryIdle.gif);
        }

        .gregory1 {
            background-image: url(../assets/GregoryTurn.webp);
        }

        .gregory2 {
            background-image: url(../assets/GregoryTurn2.gif);
        }

        .gregory3 {
            background-image: url(../assets/GregoryLose.gif);
        }

        .gregory4 {
            background-image: url(../assets/GregoryWin.webp);
        }

        .hunter {
            background-image: url(../assets/MilesIdle.webp);
        }

        .hunter0 {
            background-image: url(../assets/MilesIdle.webp);
        }

        .hunter1 {
            background-image: url(../assets/MilesTurn.webp);
        }

        .hunter2 {
            background-image: url(../assets/MilesTurn2.webp);
        }

        .hunter3 {
            background-image: url(../assets/MilesLose.webp);
        }

        .hunter4 {
            background-image: url(../assets/MilesWin.webp);
        }

        .payne {
            background-image: url(../assets/PayneIdle.webp);
        }

        .payne0{
            background-image: url(../assets/PayneIdle.webp);
        }

        .payne1{
            background-image: url(../assets/PayneTurn.webp);
        }

        .payne2{
            background-image: url(../assets/PayneTurn2.webp);
        }

        .payne3{
            background-image: url(../assets/PayneLose.webp);
        }

        .payne4{
            background-image: url(../assets/PayneWin.gif);
        }

        .franziska {
            background-image: url(../assets/FranziskaIdle.gif);
        }

        .franziska0 {
            background-image: url(../assets/FranziskaIdle.gif);
        }

        .franziska1 {
            background-image: url(../assets/FranziskaTurn.webp);
        }

        .franziska2 {
            background-image: url(../assets/FranziskaTurn2.webp);
        }

        .franziska3 {
            background-image: url(../assets/FranziskaLose.gif);
        }

        .franziska4 {
            background-image: url(../assets/FranziskaWin.gif);
        }

        .klavier {
            background-image: url(../assets/KlavierIdle.gif);
        }

        .klavier0 {
            background-image: url(../assets/KlavierIdle.gif);
        }

        .klavier1 {
            background-image: url(../assets/KlavierTurn.webp);
        }
        
        .klavier2 {
            background-image: url(../assets/KlavierTurn2.gif);
        }

        .klavier3 {
            background-image: url(../assets/KlavierWinLose.gif);
        }

        .klavier4 {
            background-image: url(../assets/KlavierWinLose.gif);
        }

        .godot {
            background-image: url(../assets/GodotIdle.gif);
        }

        .godot0 {
            background-image: url(../assets/GodotIdle.gif);
        }

        .godot1 {
            background-image: url(../assets/GodotTurn.webp);
        }

        .godot2 {
            background-image: url(../assets/GodotTurn2.webp);
        }

        .godot3 {
            background-image: url(../assets/GodotLose.webp);
        }

        .godot4 {
            background-image: url(../assets/GodotWin.webp);
        }

        .manfred {
            background-image: url(../assets/ManfredIdle.gif);
        }

        .manfred0 {
            background-image: url(../assets/ManfredIdle.gif);
        }

        .manfred1 {
            background-image: url(../assets/ManfredTurn.webp);
        }

        .manfred2 {
            background-image: url(../assets/ManfredTurn2.webp);
        }

        .manfred3 {
            background-image: url(../assets/ManfredLose.webp);
        }

        .manfred4 {
            background-image: url(../assets/ManfredWin.gif);
        }
        
    </style>