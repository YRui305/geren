<template>
    <!-- <div>主页</div> -->
    <!-- 放置一个大容器 -->
    <el-container>
        <el-aside style="height:100vh;background-color:#353b4e;width:230px">
            <layout-aside></layout-aside>
        </el-aside>
        右侧容器
        <el-container>
            <!-- 上下布局 -->
            <el-header>头部</el-header>
            <el-min>主要区域</el-min>
        </el-container>
    </el-container>
</template>

<script>
import layoutAside from '../../components/layout-aside'
export default {
  components: {
    'layout-aside': layoutAside
  }
}
</script>

<style>

</style>
