<template>
    <el-table
            :data="tableData"
            border
            style="width: 50%">
        <el-table-column
                fixed
                prop="date"
                label="日期"
                width="150">
        </el-table-column>
        <el-table-column
                prop="name"
                label="姓名"
                width="120">
        </el-table-column>

        <el-table-column
                fixed="right"
                label="操作"
                width="100">
            <template slot-scope="scope">
                <el-button @click="handleClick(scope.row)" type="text" size="small">删除</el-button>
                <el-button type="text" size="small">编辑</el-button>
            </template>
        </el-table-column>
    </el-table>
</template>

<script>
    export default {
        methods: {
            handleClick(row) {
                console.log(row);
                alert('删除成功');
                // var id = row['id'];
                // var _this = this;
                // this.$axios.post('/api/api/ushow?id='+id,)
                //     .then(function (response) {
                //         console.log(response.data.data);
                //
                //     })
                //     .catch(function (error) {
                //         console.log(error);
                //     });

            }
        },

        data() {
            return {
                tableData: [{
                    date: '2016-05-02',
                    name: '王小虎',

                }]
            }
        },
        created() {
            var _this = this;
            this.$axios.post('/api/api/ushow')
                .then(function (response) {
                    console.log(response.data.data);
                    _this.tableData = response.data.data;
                })
                .catch(function (error) {
                    console.log(error);
                });
        }
    }
</script>