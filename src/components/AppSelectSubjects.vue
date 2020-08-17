<template>
    <div>
        <select v-model="selectedSubject"
                @change="onSelected(selectedSubject)">
            <option
                    v-for="(subject, key) in subjectNames"
                    :key="key"
                    :value="key">
                <p>
                    {{subject}}
                </p>
            </option>
        </select>
        <slot name="input"></slot>
    </div>
</template>

<script>
    export default {
        name: "AppSelectSubjects",
        props: ['subjectNames'],
        data() {
            return {
                selectedSubject: 0
            };
        },
        created() {
        },
        methods: {
            onSelected: function (value) {
                this.$emit('selectedSubject', {'value': value})
            }
        }
    }
</script>

<style scoped>
    .form-items select {
        width: 373px;
        height: 43px;
        border-radius: 5px;
        margin-right: 40px;
        background: #FFFFFF;
        font-size: 15px;
        text-align: center;
    }

    .form-items input {
        width: 109px;
        height: 40px;
        border-radius: 5px;
        font-size: 18px;
        padding: 0;
    }

    option {
        background: #FFFFFF;
    }
</style>