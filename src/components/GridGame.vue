<template>
    <div></div>
</template>

    <script>
        export default {
            name: 'GridGame',
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
        div{
            --heightSize: 20vh;
            display:flex;
            width:20vh;
            height:var(--heightSize);
            border: 3px solid;
            justify-content:center;
            align-items: center;
            font-size:calc(var(--heightSize) - 10vh);
        }
    </style>