/**
 * @file index.vue
 * @author liumapp
 * @email liumapp.com@gmail.com
 * @homepage http://www.liumapp.com
 * @date 7/18/18
 */
<template>
  <div>
    <Row>
      <Col span="18" offset="3">
      <Card>
        <Steps :current="current">
          <Step title="上传合同文档" content="上传一个doc或PDF文档"></Step>
          <Step title="填写签署人" content="上传参与合同签署人的相关信息，限制为两人"></Step>
          <Step title="签署信息确认" content="后端自动生成签署人证书信息、签署位置、签章图片等相关信息"></Step>
          <Step title="下载合同文档" content="下载带有双方证书签名的合同文档"></Step>
        </Steps>
        <doc-upload v-if="current == 0" @next="nextStep" @setDocData="setDocData" :convertId="convertId"></doc-upload>
        <converting v-if="current == 1" :docList="docList" @next="nextStep" :convertId="convertId"></converting>
      </Card>
      </Col>
    </Row>
    <Row>
      <Col span="18" offset="3">
      当前在线人数：{{ people }}
      </Col>
    </Row>
  </div>
</template>
<script>
export default {
  name: 'index',
  data () {
    return {
      people: 1
    }
  }
}
</script>
