<template>
    <input type='button' id="skin" v-bind:value='name' />
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
            height:20vh;
            width:20vh;
            margin:10px;
            font-size:10vh;
        }

        
        
    </style>