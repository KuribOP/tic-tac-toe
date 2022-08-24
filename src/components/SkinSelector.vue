<template>
    <input type='button' value={{name}} />
</template>

    <script>
        export default {
            name: 'SkinSelector',
            props: {
                name:String,
            }
        }
    </script>

    <style scoped>
        input {
            height:auto;
            width:20vh;
        }
    </style>