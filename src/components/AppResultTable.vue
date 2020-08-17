<template>
    <div id="AppResultTable">
        <table class="results-table">
            <tr>
                <th><strong>Kod</strong></th>
                <th><strong>Fakultet</strong></th>
                <th><strong>Kontrakt</strong></th>
                <th><strong>Grand</strong></th>
            </tr>

            <tr v-for="(faculty, index) in successFaculties.sort(sorting)" :key="index">
                <td>{{faculty.code}}</td>
                <td style="text-align: start">{{faculty.name}}</td>
                <td>{{faculty.k}}</td>
                <td>{{faculty.g}}</td>
            </tr>
        </table>
<!--        {{a}}-->
        <!--        <table class="results-table">-->
        <!--            <tr>-->
        <!--                <th>Hudud</th>-->
        <!--                <th>Natija</th>-->
        <!--            </tr>-->
        <!--            <tr>-->
        <!--                <td style="text-align: start">-->
        <!--                    {{locations.sort(sorting)[0]}}-->
        <!--                </td>-->
        <!--                <app-result-table-items @click="a='a'" :index="1"></app-result-table-items>-->
        <!--                <td>-->
        <!--                    123-->
        <!--                </td>-->
        <!--            </tr>-->
        <!--        </table>-->
        <!--        <table class="results-table">-->
        <!--            <tr>-->
        <!--                <th>OTM</th>-->
        <!--                <th>Natija</th>-->
        <!--            </tr>-->
        <!--            <tr v-for="(university, index) in universities" :key="index">-->
        <!--                <td style="text-align: start">-->
        <!--                    {{university}}-->
        <!--                </td>-->
        <!--                <td>-->
        <!--                    123-->
        <!--                </td>-->
        <!--            </tr>-->
        <!--        </table>-->
    </div>
</template>

<script>
    import {eventEmitter} from "@/main";
    import allFaculties from "@/assets/data.json"
    import universities from "@/assets/university.json"
    import locations from "@/assets/location.json"
    import AppResultTableItems from "./AppResultTableItems";

    export default {
        name: "AppResultTable",
        data() {
            return {
                'finalBall': 0,
                allFaculties,
                'successFaculties': allFaculties,
                locations,
                universities,
                a: 'b'
            }
        },
        components: {
            // AppResultTableItems
        },
        created() {
            eventEmitter.$on('calculateResult', (value, faculties) => {
                console.log(value, faculties)
                this.successFaculties = []
                faculties.forEach((currentValue) => {
                    let my_list = this.allFaculties.filter((currentValueMap) => {
                        return currentValueMap.code.indexOf(currentValue) >= 0 && Number(value) >= Number(currentValueMap.k)
                    })
                    if (my_list.length > 0) my_list.forEach((val) => this.successFaculties.push(val))
                })
            })
        },
        methods: {
            sorting: function compare(a, b) {
                if (a < b) {
                    return -1;
                }
                if (a > b) {
                    return 1;
                }
                return 0;
            },
            isOf: () => {
                console.log('asd')
                eventEmitter.$emit('changeBool')
            }
        }
    }
</script>

<style scoped>
    #AppResultTable {
        /*justify-self: center;*/
        /*margin: 20px;*/
        width: auto;
        text-align: center;
        display: flex;
        justify-content: center;
        padding: 40px 0;
        flex-direction: column;
    }

    .results-table {
        /*font-size: 18px;*/

    }

    .results-table tr {
        height: 29px;
    }

    .results-table tr:nth-child(2n) {
        background: #85FF82;
    }

</style>