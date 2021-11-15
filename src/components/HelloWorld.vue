<template>
  <div class="record">
    <!--header-->
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
    <!--content-->
    <main class="record__main">
      <!--main title-->
      <div class="record__main-title">
        <p>Quyết định</p>
        <p>Xử phạt vi phạm hành chính theo thủ tục xử phạt không lập biên bản</p>
      </div>
      <!--main content-->
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
        <!--violation-->
        <div class="violation">
          <span class="flag">Căn cứ quyết định về việc giao quyền xử phạt vi phạm hành chính số</span>
          <el-input v-model="dataSet.value3"/>
        </div>
        <!--date-time-->
        <div class="date-time">
          <span class="flag">ngày</span>
          <el-date-picker v-model="dataSet.value4" type="date"></el-date-picker>
          <span>(nếu có);</span>
        </div>
        <!--indentity-->
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
        <!--main title-->
        <div class="record__main-title">
          <p>Quyết định:</p>
        </div>
        <!--main rule-->
        <div class="record__main-rule">
          <!--first rule-->
          <div class="first-rule">
            <span class="flag"><b>Điều 1</b>. Xử phạt bằng hình thức: </span>
            <el-autocomplete
                class="inline-input"
                v-model="dataSet.value9"
                :fetch-suggestions="querySearch6"
            ></el-autocomplete>
            <span>theo thủ tục không lập biên bản đối với:</span>
            <div class="infomation-name">
            <span class="flag">
              Ông(Bà)/Tổ chức (Tên tổ chức, người đại diện theo pháp luật)
              <span class="required">*</span>
            </span>
              <el-input v-model="dataSet.value10"/>
            </div>
            <div class="infomation-birth">
              <span class="flag">Sinh ngày</span>
              <el-date-picker v-model="dataSet.value11" type="date"></el-date-picker>
            </div>
            <div class="infomation-nationality">
              <span class="flag">Quốc tịch</span>
              <el-autocomplete
                  class="inline-input"
                  v-model="dataSet.value13"
                  :fetch-suggestions="querySearch7"
              ></el-autocomplete>
            </div>
            <div class="infomation-job">
              <span class="flag">Nghề nghiệp/Lĩnh vực hoạt động hoặc Mã số doanh nghiệp:</span>
              <el-input v-model="dataSet.value14"/>
            </div>
            <div class="infomation-address">
              <span class="flag">Nơi ở hiện tại/Địa chỉ trụ sở:</span>
              <el-input v-model="dataSet.value15"/>
            </div>
            <div class="infomation-id">
              <span class="flag">Số CMND/CCCD hoặc hộ chiếu/GCN đăng ký hoặc GP lập số:</span>
              <el-input v-model="dataSet.value16"/>
            </div>
            <div class="infomation-bonus">
              <span class="flag">Ngày cấp:</span>
              <el-date-picker v-model="dataSet.value17" type="date"></el-date-picker>

              <span class="flag">Nơi cấp:</span>
              <el-autocomplete
                  class="inline-input city"
                  v-model="dataSet.value18"
                  :fetch-suggestions="querySearch8"
              ></el-autocomplete>

              <span class="flag">Số điện thoại:</span>
              <el-input v-model="dataSet.value19"/>
            </div>
            <div class="violation-content">
              <span>Đã thực hiện hành vi vi phạm hành chính: <span class="required">*</span></span>
              <div class="area">
                <textarea></textarea>
                <span class="line"></span>
                <span class="line"></span>
                <span class="line"></span>
                <span class="line"></span>
                <span class="line"></span>
              </div>
              <div class="rules">
                <div class="block-1">
                  <span class="flag">Điểm:</span>
                  <el-input v-model="dataSet.value20"/>

                  <span class="flag">Khoản:</span>
                  <el-input v-model="dataSet.value21"/>

                  <span class="flag">Điều:</span>
                  <el-input v-model="dataSet.value22"/>

                  <span class="flag">Nghị định:</span>
                  <el-input v-model="dataSet.value23"/>

                  <span class="flag">Mức tiền phạt:</span>
                  <el-input v-model="dataSet.value24"/>
                </div>
                <div class="block-2">
                  <span class="flag">Điểm:</span>
                  <el-input v-model="dataSet.value25"/>

                  <span class="flag">Khoản:</span>
                  <el-input v-model="dataSet.value26"/>

                  <span class="flag">Điều:</span>
                  <el-input v-model="dataSet.value27"/>

                  <span class="flag">Nghị định:</span>
                  <el-input v-model="dataSet.value28"/>

                  <span class="flag">Mức tiền phạt:</span>
                  <el-input v-model="dataSet.value29"/>
                </div>
                <div class="block-3">
                  <span class="flag">Điểm:</span>
                  <el-input v-model="dataSet.value30"/>

                  <span class="flag">Khoản:</span>
                  <el-input v-model="dataSet.value31"/>

                  <span class="flag">Điều:</span>
                  <el-input v-model="dataSet.value32"/>

                  <span class="flag">Nghị định:</span>
                  <el-input v-model="dataSet.value33"/>

                  <span class="flag">Mức tiền phạt:</span>
                  <el-input v-model="dataSet.value34"/>
                </div>
              </div>
              <div class="time-and-location">
                <span class="flag">Thời gian, địa điểm xảy ra vi phạm:<span class="required">*</span> </span>
                <el-input v-model="dataSet.value35"/>
              </div>
              <div class="details">
                <span class="flag">Các tình tiết tăng nặng/ giảm nhẹ(nếu có):</span>
                <el-input v-model="dataSet.value36"/>
              </div>
              <div class="money">
                <span>Tổng mức tiền phạt chung là: {{ '950.000' }}</span>
                <span>Bằng chữ: {{ 'Chín trăm năm mươi nghìn đồng' }}</span>
              </div>
              <div class="measure">
                <span class="flag">Biện pháp ngăn chặn và bảo đảm (nếu có):</span>
                <el-input v-model="dataSet.value37"/>
              </div>
              <div class="penalize">
                <span class="flag">Hình thức xử phạt bổ sung (nếu có):</span>
                <el-input v-model="dataSet.value38"/>
              </div>
              <div class="consequence">
                <span class="flag">Biện pháp khắc phục hậu quả (nếu có):</span>
                <el-input v-model="dataSet.value39"/>
              </div>
            </div>
          </div>
          <!--second rule-->
          <div class="second-rule">
            <span>
              <b>Điều 2.</b>
              Quyết định này có hiệu lực thi hành kể từ ngày ký.
            </span>
          </div>
          <!--third rule-->
          <div class="third-rule">
            <span>
              <b>Điều 3.</b>
              Quyết định này được:
            </span>
            <div class="option-1">
              <p>a) Trong trường hợp bị phạt tiền, Ông(Bà)/Tổ chức có thể nộp phạt tại chỗ cho người có thẩm quyền xử
                phạt.</p>
              <p>
                <span class="flag">Trường hợp không nộp tiền phạt tại chỗ cho người có thẩm quyền xử phạt theo quy định tại Khoản 2 Điều 69
                Luật xử lý vi phạm hành chính thì Ông(Bà)/Tổ chức phảinộp tiền phạt tại: <span class="required">*</span>
                </span>
                <el-input v-model="dataSet.value40" />
              </p>
              <p>
                <span class="flag">trong thời hạn</span>
                <el-input v-model="dataSet.value41" />
              </p>
            </div>
            <div class="option-2"></div>
            <div class="option-3"></div>
          </div>
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
        value9: '',
        value10: '',
        value11: '',
        value12: '',
        value13: '',
        value14: '',
        value15: '',
        value16: '',
        value17: '',
        value18: '',
        value19: '',
        value20: '',
        value21: '',
        value22: '',
        value23: '',
        value24: '',
        value25: '',
        value26: '',
        value27: '',
        value28: '',
        value29: '',
        value30: '',
        value31: '',
        value32: '',
        value33: '',
        value34: '',
        value35: '',
        value36: '',
        value37: '',
        value38: '',
        value39: '',
        value40: '',
        value41: '',
        value42: '',
        value43: '',
        value44: '',
        value45: '',
        value46: '',
        value47: '',
        value48: '',
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
      listData6: [
        {
          value: 'Đội CSGT Đường Lùi số 1'
        },
        {
          value: 'Cảnh cáo'
        },
        {
          value: 'Tước quyền sử dụng giấy phép, chứng chỉ hành nghề có thời hạn'
        },
        {
          value: 'Tịch thu tang vật, phương tiện vi phạm hành chính'
        },

      ],
      listData7: [
        {
          value: 'Quốc gia 1'
        },
        {
          value: 'Quốc gia 2'
        },
        {
          value: 'Quốc gia 3'
        },
        {
          value: 'Quốc gia 4'
        },
        {
          value: 'Quốc gia 5'
        },
        {
          value: 'Quốc gia 6'
        },
      ],
      listData8: [
        {
          value: 'Thành phố 1'
        },
        {
          value: 'Thành phố 2'
        },
        {
          value: 'Thành phố 3'
        },
        {
          value: 'Thành phố 4'
        },
        {
          value: 'Thành phố 5'
        },
      ],
      listData9: [
        {
          value: 'Thành phố 1'
        },
        {
          value: 'Thành phố 2'
        },
        {
          value: 'Thành phố 3'
        },
        {
          value: 'Thành phố 4'
        },
        {
          value: 'Thành phố 5'
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
    querySearch6(queryString, cb) {
      cb(this.listData6);
    },
    querySearch7(queryString, cb) {
      cb(this.listData7);
    },
    querySearch8(queryString, cb) {
      cb(this.listData8);
    },
    querySearch9(queryString, cb) {
      cb(this.listData9);
    },
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss" scoped>
@import "HelloWorld";
</style>
