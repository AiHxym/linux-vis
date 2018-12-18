<style scoped xmlns:Card="http://www.w3.org/1999/html">
  #mainview{
    margin: 30px 0 30px 0;
    height: 25cm;
  }
  #upper{
    margin: 0 0 20px 0;
    height: 60%;
  }
  #codeview{
    border: aliceblue;
    float: left;
    width: 35%;
    height: 15cm;
  }
  #codeselecter{
    float: left;
    width: 25%;
    height: 100%;
    outline: slategrey;
  }
  #codecontent{
    float: left;
    width: 75%;
    height: 100%;
  }
  #monitor{
    width: 65%;
    height: 100%;
    float: left;
  }
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
    background-color: #515a6e;
    color: whitesmoke;
  }
  .noselect {
    -webkit-touch-callout: none; /* iOS Safari */
    -webkit-user-select: none; /* Safari */
    -khtml-user-select: none; /* Konqueror HTML */
    -moz-user-select: none; /* Firefox */
    -ms-user-select: none; /* Internet Explorer/Edge */
    user-select: none; /* Non-prefixed version, currently
                                  supported by Chrome and Opera */
  }
  .codes{
    overflow: visible;
   }
  pre code {
    background-color: rgba(255,255,255,0);
  }
</style>
<template>
  <div class="layout">
    <Layout>
      <Header>
        <Menu mode="horizontal" theme="dark" active-name="headernav" class="noselect">
          <div class="layout-logo">
            操作系统可视化
          </div>
          <div class="layout-nav">
            <MenuItem name="main">
              <Icon type="ios-construct"></Icon>
              可视化
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
              <div id="codeselecter">
                  <Menu theme="dark" width="auto" style="height: 100%" class="noselect">
                    <MenuItem name="bios">
                      BIOS
                    </MenuItem>
                    <MenuItem name="bootsectcode">
                      bootsect.S
                    </MenuItem>
                    <MenuItem name="setupcode">
                      setup.S
                    </MenuItem>
                    <MenuItem name="headcode">
                      head.S
                    </MenuItem>
                    <MenuItem name="maincode">
                      main.c
                    </MenuItem>
                  </Menu>
              </div>
              <div id="codecontent">
                <Card style="height: 100%; overflow: scroll;">
                  <pre v-highlightjs="sourcecode" class="codes"><code class="assembly">{{}}</code></pre>
                </Card>
              </div>
            </div>
            <div id="monitor">

            </div>
          </div>
          <div id="lower">
            <div id="logger">

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
