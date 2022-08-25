<template>
    <input type='button' id="skin" v-bind:value='name' />
</template>

    <script>
        export default {
            name: 'Grid',
            data() {
                return {
                }
            },
            props: {
                name:String,
            }
        }
    </script>