<template>
    <!-- <div>主页</div> -->
    <!-- 放置一个大容器 -->
    <el-container>
        <el-aside style="height:100vh;background-color:#353b4e;width:230px">
            <layout-aside></layout-aside>
        </el-aside>
        <!-- 右侧容器 -->
        <el-container>
            <!-- 上下布局 -->
            <el-header>
                <layout-header></layout-header>
            </el-header>
            <el-min>主要区域</el-min>
        </el-container>
    </el-container>
</template>

<script>
import layoutAside from '../../components/layout-aside'
import layoutHeader from '../../components/layout-header'
export default {
  components: {
    'layout-aside': layoutAside,
    'layout-header': layoutHeader
  }
}
</script>

<style>

</style>
