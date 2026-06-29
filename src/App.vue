<template>
  <el-menu
    :default-active="activeIndex"
    class="el-menu-demo"
    mode="horizontal"
    :ellipsis="false"
    @select="handleSelect"
  >
    <el-menu-item index="0">
      <img
        style="width: 50px"
        src="https://hi.mcenahle.page/logo.png"
        alt="网站徽标"
      />
      <p style="font-size: 16px">&nbsp;&nbsp;&nbsp;sponsor</p>
    </el-menu-item>
    <el-menu-item index="1">赞助页</el-menu-item>
    <el-sub-menu index="2">
      <template #title>其它网站</template>

      <el-menu-item index="2-1">
        <a
          href="https://hi.mcenahle.page"
          target="_blank"
          style="
            text-decoration: none;
            color: inherit;
            display: flex;
            justify-content: space-between;
            align-items: center;
            gap: 4px;
            width: 100%;
          "
        >
          <span>主页</span>
          <Icon icon="mdi:external-link" width="16" />
        </a>
      </el-menu-item>
      <el-menu-item index="2-2">
        <a
          href="https://blog.mcenahle.page"
          target="_blank"
          style="
            text-decoration: none;
            color: inherit;
            display: flex;
            justify-content: space-between;
            align-items: center;
            gap: 4px;
            width: 100%;
          "
        >
          <span>博客网站</span>
          <Icon icon="mdi:external-link" width="16" />
        </a>
      </el-menu-item>
    </el-sub-menu>
  </el-menu>

  <p style="color: #606266">
    请选择一种你喜欢的
    <Icon icon="mdi:payment" width="16" /> 赞助方式。
  </p>
  <p style="color: #606266">
    如需联系，也可以
    <el-link href="mailto:hi@mcenahle.page" target="_blank" underline="always"
      ><Icon icon="mdi:email-outline" width="16" />&nbsp;给我发电子邮件</el-link
    >。
  </p>

  <el-alert
    title="提示"
    type="warning"
    description="赞助大概率无法给您带来实际获益，仅代表对本人的支持。"
    show-icon
    :closable="false"
  />

  <el-tabs type="border-card" class="demo-tabs" style="margin-top: 16px">
    <el-tab-pane>
      <template #label>
        <span class="custom-tabs-label">
          <Icon icon="mdi:wechat" width="16" />
          <span> 微信</span>
        </span>
      </template>
      <div class="qrcode">
        <img src="/wechat.jpg" alt="微信" width="300" />
      </div>
    </el-tab-pane>
    <el-tab-pane>
      <template #label>
        <span class="custom-tabs-label">
          <Icon icon="simple-icons:alipay" width="16" />
          <span> 支付宝</span>
        </span>
      </template>
      <div class="qrcode">
        <img src="/alipay.jpg" alt="支付宝" width="300" />
      </div>
    </el-tab-pane>
    <el-tab-pane>
      <template #label>
        <span class="custom-tabs-label">
          <Icon icon="mdi:account-check" width="16" />
          <span> 赞助列表</span>
        </span>
      </template>
      <el-table
        border
        stripe
        :data="tableData"
        height="250"
        style="width: 100%"
      >
        <el-table-column prop="date" label="日期" width="110" />
        <el-table-column prop="name" label="名字" width="110" />
        <el-table-column prop="commits" label="评论" />
      </el-table>
    </el-tab-pane>
  </el-tabs>
</template>

<script setup>
import { Icon } from "@iconify/vue";
import { ref } from "vue";

const activeIndex = ref("1");
const handleSelect = (key, keyPath) => {
  console.log(key, keyPath);
};

const tableData = [
  {
    date: "2099-12-31",
    name: "example",
    commits: "commits",
  },
];
</script>

<style scoped>
body {
  font-family:
    -apple-system, BlinkMacSystemFont, "SF Pro Text", "SF Pro Display",
    PingFangSC, Inter, "Helvetica Neue", Helvetica, Arial, sans-serif;
}

a {
  text-decoration: none;
}

.el-menu--horizontal > .el-menu-item:nth-child(1) {
  margin-right: auto;
}

.el-menu--horizontal {
  --el-menu-horizontal-height: 50px;
}

.demo-tabs > .el-tabs__content {
  padding: 32px;
  color: #6b778c;
  font-size: 32px;
  font-weight: 600;
}

.qrcode {
  display: flex;
  justify-content: center;
}
</style>
