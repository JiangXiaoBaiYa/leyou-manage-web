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
                <tr>
                    <td class="text-xs-center">{{ props.item.id}}</td>
                    <td class="text-xs-center">{{ props.item.name }}</td>
                    <td class="text-xs-center">{{ props.item.image }}</td>
                    <td class="text-xs-center">{{ props.item.letter }}</td>
                </tr>
            </template>
        </v-data-table>
    </div>
</template>

<script>
    export default {
        name: "MyBrand",
        data() {
            return {
                totalBrands: 20, // 总条数
                brands: [], // 当前页品牌数据
                loading: true, // 是否在加载中
                pagination: {}, // 分页信息
                headers: [
                    {text: 'id', align: 'center', value: 'id'},
                    {text: '名称', align: 'center', sortable: false, value: 'name'},
                    {text: 'LOGO', align: 'center', sortable: false, value: 'image'},
                    {text: '首字母', align: 'center', value: 'letter', sortable: true,}
                ]
            }
        },
        created(){ // 渲染后执行
            // 开启加载
            this.loading = true;
            // 模拟延迟一段时间，随后进行赋值
            setTimeout(() => {
                // 然后赋值给brands
                this.brands = [
                    {"id": 2032,"name": "OPPO", "image": "1.jpg","letter": "O"},
                    {"id": 2033, "name": "飞利浦","image": "2.jpg", "letter": "F"},
                    {"id": 2034,"name": "华为","image": "3.jpg","letter": "H"},
                    {"id": 2036,"name": "酷派","image": "4.jpg","letter": "K"},
                    {"id": 2037,"name": "魅族","image": "5.jpg","letter": "M"}
                ];
                // 完成赋值后，把加载状态赋值为false
                this.loading = false;
            },2000)
        }
    }
</script>