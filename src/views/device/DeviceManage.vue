<template>
    <div>
        <a-card title="边缘设备展示">
        <a-card-grid v-for="(device) in deviceList" :key="device.deviceName" style="width:25%;text-align:center">
          <a-card hoverable style="width: 240px">
            <img
              slot="cover"
              alt="example"
              src="https://gw.alipayobjects.com/zos/rmsportal/JiqGstEfoWAOHiTxclqi.png"
            />
            <template slot="actions" class="ant-card-actions">
              <a-button type="primary" ghost>
                查看设备数据
              </a-button>
            </template>
            <a-card-meta :title="device.deviceName" :description="device.description">
              <a-avatar
                slot="avatar"
                src="https://zos.alipayobjects.com/rmsportal/ODTLcjxAfvqbxHnVXCYX.png"
              />
            </a-card-meta>
          </a-card>
        </a-card-grid>
      </a-card>
    </div>
</template>

<script>
import axios from 'axios'
export default {
  name: 'DeviceManage',
  data () {
    return {
      deviceList: []
    }
  },
  created () {
    axios.get('/cloud/device/getAllEdgeDevice').then((res) => {
      this.deviceList = res.data
      console.log(this.deviceList)
    }).catch((res) => {
      console.log(res)
    })
  }
}
</script>
