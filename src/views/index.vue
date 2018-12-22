<style>
  #mainview {
    margin: 30px 0 30px 0;
    height: 25cm;
  }

  #upper {
    margin: 0 0 20px 0;
    height: 60%;
  }

  #leftarea {
    float: left;
    width: 35%;
    height: 24cm;
  }

  #codeview {
    border: aliceblue;
    width: 100%;
    height: 70%;
  }

  #logger {
    margin-top: 20px;
    height: 25%;
    width: 100%;
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
    height: auto;
    float: left;
    text-align: center;
  }

  #register {
    display: table;
    margin: 0 auto;
  }

  #c1 {
    float: left;
    margin: 0 5px 0 5px;
  }

  #c2 {
    float: left;
    margin: 0 5px 0 5px;
  }

  #c3 {
    float: left;
    margin: 0 5px 0 5px;
  }

  #c4 {
    float: left;
    margin: 0 5px 0 5px;
  }

  #c5 {
    float: left;
    margin: 0 5px 0 5px;
  }

  #ramusage {
    display: table;
    height: 2cm;
    width: 80%;
    margin: 0 auto;

  }

  #diskusage {
    display: table;
    margin: 0 auto;
  }

  #disk {
    float: left;
    width: 600px;
    height: 60px;
    margin: 30px 0 30px 20px;
  }

  #circle {
    float: left;
  }

  #buttonbar {
    margin-bottom: 10px;
    width: 100%;
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

  h2 {
    margin: 10px 0 10px 0;
  }
</style>
<template>
  <div class="layout">
    <Layout>
      <Header>
        <Menu mode="horizontal" theme="dark" active-name="headernav" class="noselect">
          <div class="layout-logo">
            <h3>操作系统可视化</h3>
          </div>
          <div class="layout-nav">
            <MenuItem name="main">
              <Icon type="md-desktop"></Icon>
              可视化
            </MenuItem>
            <MenuItem name="data">
              <Icon type="md-folder"></Icon>
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
            <div id="leftarea">
              <div id="buttonbar">
                <ButtonGroup shape="circle" style="margin: 0 auto; display: table">
                  <Button type="default" icon="ios-skip-backward"></Button>
                  <Button type="default" icon="ios-play" v-bind:icon="iconStatus" @click="changeIcon"></Button>
                  <Button type="default" icon="ios-skip-forward"></Button>
                </ButtonGroup>
              </div>
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
                  <code class="assembly cpp"
                        style="background-color: rgba(0, 0, 0, 0);color: #444444;overflow: visible; height: auto"></code>
                </pre>
                </div>
              </div>
              <div id="logger">
                <Tabs value="name1" style="width: 100%; height: 100%">
                  <TabPane label="标签一" name="name1">
                    <div id="loggerbar"
                         style="width: 100%; height: 10%; background:rgba(0, 0, 0, 0.2);">
                      <img src="./../assets/images/console.svg" alt="console" style="height: 100%; width: auto">
                    </div>
                    <textarea id="loggercontent"
                              style="width: 100%; height: 90%; background-color: black; color: white; resize:none; "></textarea>
                  </TabPane>
                  <TabPane label="标签二" name="name2">标签二的内容</TabPane>
                  <TabPane label="标签三" name="name3">标签三的内容</TabPane>
                </Tabs>

              </div>
            </div>
            <div id="monitor">
              <h2>寄存器数据</h2>
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
              <h2 style="margin-top: 20px">内存使用情况</h2>
              <div id="ramusage">
                <Tooltip placement="top" theme="dark" v-for="item in rams" style="float: left; height: 100%"
                         :style="{width: item.size, backgroundColor: item.color}" :key="item.name">
                  <div slot="content">
                    <p><h3>{{item.name}}</h3></p>
                    <p><span>{{item.addr}}</span></p>
                  </div>
                </Tooltip>
              </div>
              <h2 style="margin-top: 30px; margin-bottom: 5px">磁盘状态</h2>
              <div id="diskusage">
                <div id="circle">
                  <Circle :percent="percent" :stroke-color="color">
                    <Icon v-if="percent == 100" type="ios-checkmark" size="60" style="color:#5cb85c"></Icon>
                    <span v-else style="font-size:24px">{{ percent }}%</span>
                  </Circle>
                </div>
                <div id="disk">
                  <Tooltip placement="top" content="boot扇区"
                           style="background-color: #808695; width: 10%; height: 100%; float: left;"></Tooltip>
                  <Tooltip placement="top" content="setup模块"
                           style="background-color: #2d8cf0; width: 40%; height: 100%; float:left;"></Tooltip>
                  <Tooltip placement="top" content="system模块"
                           style="background-color: #19be6b; width: 50%; height: 100%; float:left;"></Tooltip>
                </div>
              </div>
            </div>
          </div>
          <div id="lower">


          </div>
        </div>
      </Content>
      <Footer class="layout-footer-center">2018 &copy; AiHxym</Footer>
    </Layout>
  </div>
</template>
<script>
  import datas from '@/assets/mock/data.json';
  import Vue from  'vue';
  export default {

    data() {
      return {
        decrease: 0,
        iconStatus: "ios-play",
        percent: 0,
        content: "",
        rams: [],
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
            name: 'EAX',
            value: '0'
          },
          {
            name: 'EBX',
            value: '0'
          },
          {
            name: 'ECX',
            value: '0'
          },
          {
            name: 'EDX',
            value: '0'
          }
        ],
        columns2: [
          {
            title: 'AX',
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
    computed: {
      color() {
        let color = '#2db7f5';
        if (this.percent === 100) {
          color = '#5cb85c';
        }
        return color;
      }
    },
    methods: {
      getContent(name) {
        this.content = datas.code.find(e => e.name === name).content;
      },
      add() {
        if (this.percent >= 100) {
          return false;
        }
        this.percent += 1;
      },
      minus() {
        if (this.percent <= 0) {
          return false;
        }
        this.percent -= 1;
      },
      changeIcon() {
        if (this.iconStatus === "ios-pause") {
          this.iconStatus = "ios-play";
        } else {
          this.iconStatus = "ios-pause";
          setTimeout(()=> this.parseEvent(1, 0),
          10000
          );

        }
      },
      parseEvent(index, number) {
        if (index === 1) {
          var event = datas.events.bootsect[number];
          for (let i in event.ram){
            this.rams.push(event.ram[i]);
          }
          if(event.isCarry === true)
          {
            var cnt = 1;
            var decrease = parseInt(event.ram[event.carry.from].size) / event.carry.times;
            var tmp = setInterval(()=>{
              if(cnt >= event.carry.times) {

                clearInterval(tmp);
              }
              let size = (parseFloat(this.rams[event.carry.from - 1].size) + decrease).toString() + '%';
              Vue.set(this.rams, event.carry.from - 1, {
                "size": size,
                "name": this.rams[event.carry.from - 1].name,
                "addr": this.rams[event.carry.from - 1].addr,
                "color": this.rams[event.carry.from - 1].color
              });
              size = (parseFloat(this.rams[event.carry.from].size) - decrease).toString() + '%';
              Vue.set(this.rams, event.carry.from, {
                "size": size,
                "name": this.rams[event.carry.from].name,
                "addr": this.rams[event.carry.from].addr,
                "color": this.rams[event.carry.from].color
              });
              size = (parseFloat(this.rams[event.carry.to + 1].size) - decrease).toString() + '%';
              Vue.set(this.rams, event.carry.to + 1, {
                "size": size,
                "name": this.rams[event.carry.to + 1].name,
                "addr": this.rams[event.carry.to + 1].addr,
                "color": this.rams[event.carry.to + 1].color
              });
              size = (parseFloat(this.rams[event.carry.to].size) + decrease).toString() + '%';
              Vue.set(this.rams, event.carry.to, {
                "size": size,
                "name": this.rams[event.carry.to].name,
                "addr": this.rams[event.carry.to].addr,
                "color": this.rams[event.carry.to].color
              });
              cnt += 1;
            },50);
          } else {
            for (let i in event.ram){
              this.rams.push(event.ram[i]);
            }
          }

        } else if (index === 2) {

        } else if (index === 3) {

        }

      }
    }
  }
</script>
