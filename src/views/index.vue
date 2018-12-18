<style scoped>
  .layout{
    border: 1px solid #d7dde4;
    background: #f5f7f9;
    position: relative;
    border-radius: 4px;
    overflow: hidden;

  }
  .layout-logo{
    width: 150px;
    height: 30px;
    background: #5b6270;
    border-radius: 3px;
    float: left;
    position: relative;
    top: 15px;
    left: 20px;
    text-align:center;
    line-height: 30px;
    font-weight: bold;
    color: aliceblue;
  }
  .layout-nav{
    float: right;
    margin: 0 auto;
    margin-right: 20px;
  }
  .layout-footer-center{
    text-align: center;
  }
</style>
<template>
  <div class="layout">
    <Layout>
      <Header>
        <Menu mode="horizontal" theme="dark" active-name="1">
          <div class="layout-logo">
            操作系统可视化
          </div>
          <div class="layout-nav">
            <MenuItem name="main">
              <Icon type="ios-construct"></Icon>
              主页
            </MenuItem>
            <MenuItem name="data">
              <Icon type="ios-folder"></Icon>
              查看数据
            </MenuItem>
            <MenuItem name="about">
              <Icon type="ios-information-circle-outline"></Icon>
              关于
            </MenuItem>
          </div>
        </Menu>
      </Header>
      <Content :style="{padding: '0 50px'}">
        <div id="mainview">
          <div id="upper">
            <div id="codeview">

            </div>
            <div id="monitor">

            </div>
          </div>

        </div>
      </Content>
      <Footer class="layout-footer-center">2018 &copy; AiHxym</Footer>
    </Layout>
  </div>
</template>
<script>
  export default {

  }
</script>
