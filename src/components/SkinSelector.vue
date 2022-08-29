<template>
    <input type='button' id="skin" v-bind:class='name' class='mugshot' />
</template>

    <script>
        export default {
            name: 'SkinSelector',
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
        input {
            height:15vh;
            width:15vh;
            margin:1%;
        }
        
        .mugshot{
             background-size:100% 100%;
        }

        .phoenix {
            background-image: url(../assets/Mugshot-phoenix.webp);
        }

        .mia {
            background-image: url(../assets/Mugshot-mia.webp);
        }

        .apollo {
            background-image: url(../assets/Mugshot-apollo.png);
        }

        .athena {
            background-image: url(../assets/Mugshot-athena.png);
        }

        .gregory {
            background-image: url(../assets/Mugshot-gregory.png);
        }

        .hunter {
            background-image: url(../assets/Mugshot-miles.webp);
        }

        .franziska {
            background-image: url(../assets/Mugshot-franziska.webp);
        }

        .klavier {
            background-image: url(../assets/Mugshot-klavier.png);
        }

        .godot {
            background-image: url(../assets/Mugshot-godot.webp);
        }

        .manfred {
            background-image: url(../assets/Mugshot-manfred.webp);
        }

        .payne {
            background-image: url(../assets/Mugshot-payne.webp);
        }

        
    </style>