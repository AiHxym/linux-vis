<style>
  #mainview {
    margin: 30px 0 30px 0;
    height: 25cm;
  }

  #upper {
    margin: 0 0 20px 0;
    height: 60%;
  }

  #codeview {
    border: aliceblue;
    float: left;
    width: 35%;
    height: 15cm;
  }

  #codeselecter {
    float: left;
    width: 20%;
    height: 100%;
    outline: slategrey;
  }

  #codecontent {
    float: left;
    width: 80%;
    height: 100%;
    overflow: scroll;
    background-color: #dcdee2;
  }

  #monitor {
    width: 65%;
    height: 100%;
    float: left;
    text-align: center;
  }

  #register {
    display: table;
    margin: 0 auto;
  }

  #c1 {
    float: left;
  }

  #c2 {
    float: left;
  }

  #c3 {
    float: left;
  }

  #c4 {
    float: left;
  }

  #c5 {
    float: left;
  }

  .layout {
    border: 1px solid #d7dde4;
    background: #f5f7f9;
    position: relative;
    border-radius: 4px;
    overflow: hidden;

  }

  .layout-logo {
    width: 150px;
    height: 30px;
    background: #5b6270;
    border-radius: 3px;
    float: left;
    position: relative;
    top: 15px;
    left: 20px;
    text-align: center;
    line-height: 30px;
    font-weight: bold;
    color: aliceblue;
  }

  .layout-nav {
    float: right;
    margin: 0 auto;
    margin-right: 20px;
  }

  .layout-footer-center {
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
    user-select: none;
    /* Non-prefixed version, currently
                                     supported by Chrome and Opera */
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
              <div id="codeselecter" class="noselect">
                <Menu theme="dark" width="auto" style="height: 100%">
                  <MenuItem name="bios" @click.native="getContent('BIOS')">
                    BIOS
                  </MenuItem>
                  <MenuItem name="bootsectcode" @click.native="getContent('bootsect.S')">
                    bootsect.S
                  </MenuItem>
                  <MenuItem name="setupcode" @click.native="getContent('setup.S')">
                    setup.S
                  </MenuItem>
                  <MenuItem name="headcode" @click.native="getContent('head.S')">
                    head.S
                  </MenuItem>
                  <MenuItem name="maincode" @click.native="getContent('main.c')">
                    main.c
                  </MenuItem>
                </Menu>
              </div>
              <div id="codecontent">
                <pre v-highlightjs="content"
                     style="background-color: rgba(0, 0, 0, 0);color: #444444;overflow: visible; height: auto">
                  <code class="assembly"
                        style="background-color: rgba(0, 0, 0, 0);color: #444444;overflow: visible; height: auto"></code>
                </pre>
              </div>

            </div>
            <div id="monitor">
              <div id="register">
                <div id="c1">
                  <Table border stripe :columns="columns1" :data="data1"></Table>
                </div>
                <div id="c2">
                  <Table border stripe :columns="columns2" :data="data2"></Table>
                </div>
                <div id="c3">
                  <Table border stripe :columns="columns3" :data="data3"></Table>
                </div>
                <div id="c4">
                  <Table border stripe :columns="columns4" :data="data4"></Table>
                </div>
                <div id="c5">
                  <Table border stripe :columns="columns5" :data="data5"></Table>
                </div>
              </div>

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
  import datas from '@/assets/mock/data.json'

  export default {

    data() {
      return {
        content: "",
        columns1: [
          {
            title: 'Name',
            key: 'name'
          },
          {
            title: 'Value',
            key: 'value'
          }
        ],
        data1: [
          {
            name: 'R1',
            value: '0'
          },
          {
            name: 'R2',
            value: '0'
          }
        ],
        columns2: [
          {
            title: 'Name',
            key: 'name'
          },
          {
            title: 'Value',
            key: 'value'
          }
        ],
        data2: [
          {
            name: 'R1',
            value: '0'
          },
          {
            name: 'R2',
            value: '0'
          }
        ],
        columns3: [
          {
            title: 'Name',
            key: 'name'
          },
          {
            title: 'Value',
            key: 'value'
          }
        ],
        data3: [
          {
            name: 'R1',
            value: '0'
          },
          {
            name: 'R2',
            value: '0'
          }
        ],
        columns4: [
          {
            title: 'Name',
            key: 'name'
          },
          {
            title: 'Value',
            key: 'value'
          }
        ],
        data4: [
          {
            name: 'R1',
            value: '0'
          },
          {
            name: 'R2',
            value: '0'
          }
        ],
        columns5: [
          {
            title: 'Name',
            key: 'name'
          },
          {
            title: 'Value',
            key: 'value'
          }
        ],
        data5: [
          {
            name: 'R1',
            value: '0'
          },
          {
            name: 'R2',
            value: '0'
          }
        ]
      }
    },
    methods: {
      getContent(name) {
        this.content = datas.code.find(e => e.name === name).content;
      }
    }
  }
</script>
