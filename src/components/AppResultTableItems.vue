<template>
    <div>
        <span v-if="isMy">
             a
        </span>
        abs
    </div>
</template>

<script>
    import {eventEmitter} from "../main";

    export default {
        name: "AppResultTableItems",
        data() {
            return {
                isMy: false
            }
        },
        props: [
            'index'
        ],
        created() {
            // eventEmitter.$on('changeBool', () => {
            //     this.isMy = !this.isMy
            //     console.log(123)
            // })
        }
    }
</script>

<style scoped>

</style>