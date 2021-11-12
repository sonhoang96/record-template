<template>
  <div class="record">
    <header class="record__header">
      <div class="record__header-left">
        <p>Phòng cảnh sát giao thông Đà Nẵng</p>
        <p>Trạm CSGT cửa ô hòa hiệp</p>
        <p>Số:19C126304/BB-VPHC</p>
        <p class="permission">
          <span class="flag">Quyển số: </span>
          <el-input v-model="dataSet.value1"/>
        </p>
      </div>
      <div class="record__header-right">
        <span>Mẫu số 01/QĐ-XPKLBB <br/>Ban hành kèm theo Thông tư số 07/2019/TT-BCA <br/> ngày 20/3/2019</span>
        <p>CỘNG HÒA XÃ HỘI CHỦ NGHĨA VIỆT NAM</p>
        <p>Độc lập - Tự do - Hạnh phúc</p>
        <p>
          <i>Hà Nội, ngày 28 tháng 09 năm 2021</i>
        </p>
      </div>
    </header>
    <main class="record__main">
      <div class="record__main-title">
        <p>Quyết định</p>
        <p>Xử phạt vi phạm hành chính theo thủ tục xử phạt không lập biên bản</p>
      </div>
      <div class="record__main-content">
        <p>Căn cứ Điều 56 Luật xử lý vi phạm hành chính;</p>
        <div class="based-on">
          <span class="flag">Căn cứ <b class="required">*</b></span>
          <el-autocomplete
              class="inline-input"
              v-model="dataSet.value2"
              :fetch-suggestions="querySearch1"
          ></el-autocomplete>
        </div>
        <p>Căn cứ hồ sơ vụ vi phạm do cơ quan tiến hành tố tụng hình sự chuyển đến (nếu có);</p>
        <p>Căn cứ kết quả xác minh và các tài liệu có trong hồ sơ;</p>
        <div class="violation">
          <span class="flag">Căn cứ quyết định về việc giao quyền xử phạt vi phạm hành chính số</span>
          <el-input v-model="dataSet.value3"/>
        </div>
        <div class="date-time">
          <span class="flag">ngày</span>
          <el-date-picker v-model="dataSet.value4" type="date"></el-date-picker>
          <span>(nếu có);</span>
        </div>
        <div class="indentity">
          <span class="flag">Tôi <b class="required">*</b></span>
          <el-autocomplete
              class="inline-input"
              v-model="dataSet.value5"
              :fetch-suggestions="querySearch2"
          ></el-autocomplete>

          <span class="flag">Cấp bậc</span>
          <el-autocomplete
              disabled
              class="inline-input"
              v-model="dataSet.value6"
              :fetch-suggestions="querySearch3"
          ></el-autocomplete>

          <span class="flag">Chức vụ</span>
          <el-autocomplete
              disabled
              class="inline-input"
              v-model="dataSet.value7"
              :fetch-suggestions="querySearch4"
          ></el-autocomplete>

          <span class="flag">Đơn vị</span>
          <el-autocomplete
              disabled
              class="inline-input"
              v-model="dataSet.value8"
              :fetch-suggestions="querySearch5"
          ></el-autocomplete>
        </div>

        <div class="record__main-title">
          <p>Quyết định:</p>
        </div>
      </div>
    </main>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },
  data: () => {
    return {
      dataSet: {
        value1: '',
        value2: '',
        value3: '',
        value4: '',
        value5: '',
        value6: '',
        value7: '',
        value8: '',
      },
      listData1: [
        {
          value: 'Quyết định 1'
        },
        {
          value: 'Quyết định 2'
        },
        {
          value: 'Quyết định 3'
        },
      ],
      listData2: [
        {
          value: 'Hoàng Tử Gió'
        },
        {
          value: 'Chương Tam Phong'
        },
        {
          value: 'Hồng Lâu Mộng'
        },
      ],
      listData3: [
        {
          value: 'Thiếu dương'
        },
        {
          value: 'Thiếu âm'
        },
        {
          value: 'Thái tuế'
        },

      ],
      listData4: [
        {
          value: 'Thầy tu mù'
        },
        {
          value: 'Đứa con của gió'
        },
        {
          value: 'Anh bán chiếu'
        },

      ],
      listData5: [
        {
          value: 'Đội CSGT Đường Lùi số 1'
        },
        {
          value: 'Đội CSGT Đường Đường Chính Chính'
        },
        {
          value: 'Đội CSGT Đường Phèn Số 2'
        },

      ],
    }
  },
  methods: {
    querySearch1(queryString, cb) {
      cb(this.listData1);
    },
    querySearch2(queryString, cb) {
      cb(this.listData2);
    },
    querySearch3(queryString, cb) {
      cb(this.listData3);
    },
    querySearch4(queryString, cb) {
      cb(this.listData4);
    },
    querySearch5(queryString, cb) {
      cb(this.listData5);
    },
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss" scoped>
@import "HelloWorld";
</style>
