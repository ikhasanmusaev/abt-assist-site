<template>
    <div id="AppResultForm">
        <form action="#">
            <app-select-subjects
                    class="form-items"
                    :subjectNames="subjectNames"
                    @selectedSubject="filteredByA($event.value)"
            >
                <input slot="input" type="number" v-model.trim="inputA" @input="updateValue"
                       @blur="$v.inputA.$touch()">
            </app-select-subjects>
            <app-select-subjects
                    class="form-items"
                    :subjectNames="subjectNamesB"
                    @selectedSubject="filteredByB($event.value)"
            >
                <input slot="input" type="number" v-model.trim="inputB" @input="updateValue"
                       >
            </app-select-subjects>

            <app-select-subjects
                    class="form-items"
                    :subjectNames="subjectNamesC"
                    @selectedSubject="filteredByC($event.value)"
            >
                <input slot="input" type="number" v-model="inputC" @input="updateValue"
                       >
            </app-select-subjects>
        </form>
        <button
                type="submit"
                @click="calculate"
                :disabled="finalFaculties.length < 1 || $v.$invalid"
        >
            Hisoblash
        </button>
    </div>
</template>

<script>
    import subjectNames from '@/assets/subjectNames.json';
    import subjectsData from '@/assets/subjects.json';
    import AppSelectSubjects from "@/components/AppSelectSubjects";
    import {eventEmitter} from "@/main";
    import {between, required} from 'vuelidate/lib/validators'

    export default {
        name: "AppResultForm",
        components: {
            AppSelectSubjects
        },
        data() {
            return {
                subjectsData,
                subjectNames,
                subjectNamesB: {"0": "2-Fanni tanlang!",},
                subjectNamesC: {"0": "3-Fanni tanlang!",},
                finalFaculties: [],
                subjectA: '',
                subjectB: '',
                subjectC: '',
                inputA: '',
                inputB: '',
                inputC: '10',
            }
        },
        methods: {
            updateValue() {
                if (Number(this.inputA) > 30) this.inputA = 30
                if (Number(this.inputB) > 30) this.inputB = 30
                if (Number(this.inputC) > 30) this.inputC = 30
                if (Number(this.inputA) < 0) this.inputA = 0
                if (Number(this.inputB) < 0) this.inputB = 0
                if (Number(this.inputC) < 0) this.inputC = 0
            },
            filteredByA(value) {
                this.subjectA = value
                this.subjectNamesB = {"0": "2-Fanni tanlang!",}
                let filteredSubjectsA = this.subjectsData.filter(function (array) {
                    return array[0] === value
                });
                filteredSubjectsA.forEach(currentValue => {
                    let filteredValue = Object.keys(this.subjectNames).find(key => key === currentValue[1]);

                    if (filteredValue) {
                        this.subjectNamesB[filteredValue] = this.subjectNames[filteredValue]
                    }
                });
                for (let i = this.subjectNamesB.length - 1; i >= 0; i--) {
                    if (this.subjectNamesB.indexOf(this.subjectNamesB[i]) !== i)
                        this.subjectNamesB.splice(i, 1);
                }
            },
            filteredByB(value) {
                this.subjectB = value
                this.subjectNamesC = {"0": "3-Fanni tanlang!",}
                let filteredSubjectsB = this.subjectsData.filter((array) => {
                    return array[0] + array[1] === this.subjectA + this.subjectB
                });
                filteredSubjectsB.forEach(currentValue => {
                    let filteredValue = Object.keys(this.subjectNamesB).find(key => key === currentValue[2]);
                    if (filteredValue) {
                        this.subjectNamesC[filteredValue] = this.subjectNames[filteredValue]
                    }
                });
                // for (let i = this.subjectNamesC.length - 1; i >= 0; i--) {
                //     if (this.subjectNamesC.indexOf(this.subjectNamesC[i]) !== i)
                //         this.subjectNamesC.splice(i, 1);
                // }
            },
            filteredByC(value) {
                this.subjectC = value
                this.finalFaculties = []
                let filteredSubjectsC = this.subjectsData.filter((array) => {
                    return array[0] + array[1] + array[2] === this.subjectA + this.subjectB + this.subjectC
                });
                filteredSubjectsC.forEach(currentValue => {
                    let finalFaculty = currentValue.slice(3)
                    if (finalFaculty) {
                        this.finalFaculties.push(finalFaculty)
                    }
                });
            },
            calculate() {
                const endValue = Number(this.inputA) * 3.1 + Number(this.inputB) * 2.1 + Number(this.inputC) * 1.1
                let faculties = this.finalFaculties

                for (let i = faculties.length - 1; i >= 0; i--) {
                    if (faculties.indexOf(faculties[i]) !== i)
                        faculties.splice(i, 1);
                }
                    eventEmitter.$emit('calculateResult', endValue, faculties)
            }
        },
        validations: {
            inputA: {
                required,
                between: between(1, 30)
            },
            inputB: {
                required,
                between: between(1, 30)
            },
            inputC: {
                between: between(1, 30)
            }
        }
    }
</script>

<style scoped>
    #AppResultForm {
        display: flex;
        background: #f0fdff;
        flex-direction: column;
        align-self: start;
        /*padding: 20px;*/
        width: 100%;
    }

    #AppResultForm form {
        margin: 20px;
    }

    .form-items {
        margin: 20px;
        display: flex;
        align-items: center;
    }

    .form-items select {
        width: 373px;
        height: 43px;
        border-radius: 5px;
        margin-right: 40px;
    }

    .form-items input {
        width: 109px;
        height: 40px;
        border-radius: 5px;
        font-size: 18px;
        padding: 0;
    }

    button {
        width: 150px;
        height: 50px;
        align-self: center;
        font-size: 20px;
        margin-bottom: 20px;
        background: #85FF82;
        border: none;
        border-radius: 7px;
        cursor: pointer;
    }

    button:disabled {
        cursor: default;
    }

</style>