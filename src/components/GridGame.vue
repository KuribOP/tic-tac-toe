<template>
    <div class='tokenSize'></div>
</template>

    <script>
        export default {
            name: 'GridGame',
            data() {
                return {
                }
            },
            props: {
                row:Number,
            }
        }
    </script>

    <style scoped>
        div{
            --heightSize:calc(100/row);
            width:20vh;
            height:var(--heightSize);
            border: 3px solid;
        }

        .tokenSize{
            background-size:100% 100%;
        }

        .blueGotIt{
            background-image: url(../assets/blueGotIt.png);
        }
        .blueHoldIt{
            background-image: url(../assets/blueHoldIt.png);
        }
        .blueObjection{
            background-image: url(../assets/blueObjection.png);
        }
        .blueTakeThat{
            background-image: url(../assets/blueTakeThat.png);
        }
        
        .redGotIt{
            background-image: url(../assets/redGotIt.png);
        }
        .redHoldIt{
            background-image: url(../assets/redHoldIt.png);
        }
        .redObjection{
            background-image: url(../assets/redObjection.png);
        }
        .redTakeThat{
            background-image: url(../assets/redTakeThat.png);
        }

    </style>