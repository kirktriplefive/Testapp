<template>
    <div>
        <ul>
            <spisok
            v-for="(lib, i) of librir"
            v-bind:lib="lib"
            v-on:remove-lib="removelib"
            v-on:edit-lib="editLib"
            v-on:savelib="savelib"
            v-bind:index="i"
            />
        </ul>
    </div>
</template>

<script >
    import spisok from '@/components/liiiil'
    export default {
        props: ['librir'],
        components: {
            spisok
        },
        methods: {
            removelib(id) {
                this.$emit('remove-lib', id)
            },
            editLib(id) {
                this.$emit('edit-lib', id)
            }
        }
    }
</script>

<style scoped>
</style>