<template xmlns:v-slot="http://www.w3.org/1999/XSL/Transform">
    <div>

        <v-data-table
                :headers="headers"
                :items="brands"
                :pagination.sync="pagination"
                :total-items="totalBrands"
                :loading="loading"
                class="elevation-1"
        >
            <template v-slot:items="props">
                <td class="text-xs-center">{{ props.item.id }}</td>
                <td class="text-xs-center">{{ props.item.name }}</td>
                <td class="text-xs-center">{{ props.item.image }}</td>
                <td class="text-xs-center">{{ props.item.letter }}</td>
                <td class="text-xs-center">
                    <v-btn color="warning" fab flat append>
                        <v-icon>fas fa-edit</v-icon>
                    </v-btn>
                    <v-btn color="info">Info</v-btn>
                </td>

            </template>
        </v-data-table>
    </div>
</template>

<script>
    export default {
        name: "MyBrand",
        data () {
            return {
                totalBrands: 0,
                brands: [],
                loading: true,
                pagination: {},
                headers: [

                    {text: '品牌ID', align: 'center',  value: 'id'},
                    { text: '品牌名称',align: 'center', sortable: false,value: 'name' },
                    { text: '品牌LOGO', align: 'center',sortable: false,value: 'image' },
                    { text: '品牌首字母',align: 'center',value: 'letter' },
                    { text: '操作',align: 'center',value: 'option' },

                ]
            }
        },
        methods:{
            getDataFromServer() {
                //发起请求
                this.$http.get("/item/brand/page").then(
                    resp =>{
                        console.log(resp)
                    }
                );
            }
        },
        created() {
            this.loading = true;
            setTimeout(() => {
                this.brands = [
                    {"id": 2032, "name": "OPPO", "image": "1.jpg", "letter": "O"},
                    {"id": 2033, "name": "飞利浦", "image": "2.jpg", "letter": "F"},
                    {"id": 2034, "name": "华为", "image": "3.jpg", "letter": "H"},
                    {"id": 2036, "name": "酷派", "image": "4.jpg", "letter": "K"},
                    {"id": 2037, "name": "魅族", "image": "5.jpg", "letter": "M"}
                ];
                this.loading = false;
            }, 200);
        }
    }
</script>
content_copy
