<template>
    <el-row>
        <el-row class="layout-header" type="flex" align="middle">
            <el-col class="left" :span="12">
                <!-- 左侧 -->
                <i class="el-icon-s-fold"></i>
                <span>江苏传智播客教育科技有限公司</span>
            </el-col>
            <el-col class="right" :span="12">
                <el-row type='flex' justify="end" align="middle">
                    <img src="../assets/img/hd.jpg" alt="">
                    <el-dropdown>
                        <span>隔壁老王</span>
                        <el-dropdown-menu slot="dropdown">
                            <el-dropdown-item>个人信息</el-dropdown-item>
                            <el-dropdown-item>git地址</el-dropdown-item>
                            <el-dropdown-item>返回</el-dropdown-item>
                            <el-dropdown-item>退出</el-dropdown-item>
                        </el-dropdown-menu>
                    </el-dropdown>
                </el-row>

            </el-col>
        </el-row>
    </el-row>
<!-- <div>toubu</div> -->
</template>

<script>
export default {

}
</script>

<style lang='less' scoped>
    .layout-header{
        height: 60px;
        .left{
            font-size: 20px;
            span{
                color: #2c3e50;
                font-size: 16px;
                margin-left: 4px;
            }

        }
        .right{
            img{
                width: 40px;
                height: 40px;
                border-radius: 50%;
                margin-right: 5px;
            }
        }
    }
</style>
