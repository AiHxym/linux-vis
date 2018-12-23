<template>
  <Layout>
    <Header>
      <Menu mode="horizontal" theme="dark" active-name="headernav" class="noselect">
        <div class="layout-logo">
          <h3>操作系统可视化</h3>
        </div>
        <div class="layout-nav">
          <router-link to="/">
            <MenuItem name="main">
              <Icon type="md-desktop"></Icon>
              可视化
            </MenuItem>
          </router-link>
          <router-link to="/datas">
            <MenuItem name="Datas">
              <Icon type="md-eye"></Icon>
              查看数据
            </MenuItem>
          </router-link>
          <router-link to="/about">
            <MenuItem name="about">
              <Icon type="ios-information-circle-outline"></Icon>
              关于
            </MenuItem>
          </router-link>
        </div>
      </Menu>
    </Header>
    <Content style="padding: 30px 50px 30px 50px; min-height: 1000px">
      <div>
        <JsonView :json="JsonData"></JsonView>
      </div>
    </Content>
    <Footer class="layout-footer-center">2018 Copyright &copy; AiHxym</Footer>
  </Layout>
</template>

<script>
  import JsonView from '@/components/JsonView'
  import datas from '@/assets/mock/data.json'

  export default {
    name: 'test',
    data() {
      return {
        JsonData: datas.events
      }
    },
    components: {JsonView}
  }
</script>
