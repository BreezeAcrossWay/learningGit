<template>
  <div class="app-container">
    <div class="card">
      <div>
        <p class="title"><img src="@/assets/imgs/doctor.png" alt="">&nbsp;{{ info.name }}医生</p>
      </div>
      <div class="pho">
        <p class="photo"><img :src="`${info.avatar}`" alt=""></p>
      </div>
      <div class="info">
        <div class="box">
          <span>Account</span>
          <span>{{ info.allUserInfo.name }} <img src="@/assets/imgs/user.png" alt=""></span>
        </div>
        <div class="box">
          <span>Mail</span>
          <span>{{ info.allUserInfo.mail }} <img src="@/assets/imgs/mail.png" alt=""></span>
        </div>
        <div class="box">
          <span>Phone</span>
          <span>{{ info.allUserInfo.phone }} <img src="@/assets/imgs/phone.png" alt=""></span>
        </div>
      </div>
    </div>
    <div class="func">
      <div>
        <p class="title"><img src="@/assets/imgs/func.png" alt="">&nbsp;核心功能</p>
      </div>
      <div class="add">
        <div class="text">
          <p>添加</p>
          <p>疑似病患</p>
        </div>
        <div class="addimg" @click="dialogFormVisible = true"><img src="@/assets/imgs/add.png" alt=""></div>
      </div>
      <div class="upload">
        <div class="text">
          <p>上传</p>
          <p>病患图片</p>
        </div>
        <div class="addimg" @click="dialogDetection = true"><img src="@/assets/imgs/add.png" alt=""></div>
      </div>
    </div>
    <el-dialog title="添加疑似病患" :visible.sync="dialogFormVisible" center>
      <el-form label-width="80px" label-position="left">
        <el-form-item label="上传头像">
          <!-- <el-input placeholder="Role Name" /> -->
          <el-upload
            action="https://jsonplaceholder.typicode.com/posts/"
            list-type="picture-card"
            :on-preview="handlePictureCardPreview"
            :on-remove="handleRemove"
          >
            <i class="el-icon-plus" />
          </el-upload>
          <el-dialog :visible.sync="dialogVisible">
            <img width="100%" :src="dialogImageUrl" alt="">
          </el-dialog>
        </el-form-item>
        <el-form-item label="姓名">
          <el-input v-model="form.name" placeholder="Please input your Name" />
        </el-form-item>
        <el-form-item label="手机号">
          <el-input v-model="form.number" placeholder="Please input your phonenumber" />
        </el-form-item>
        <el-form-item label="邮箱">
          <el-input v-model="form.mail" placeholder="Please input your mailbox" />
        </el-form-item>
      </el-form>
      <span slot="footer" class="dialog-footer">
        <el-button type="primary" @click="centerdialogFormVisible = false">提 交</el-button>
      </span>
    </el-dialog>
    <el-dialog title="上传检测图片" :visible.sync="dialogDetection" center>
      <el-form label-width="80px" label-position="left">
        <el-form-item label="检测类型">
          <el-select v-model="detect" placeholder="请选择">
            <el-option
              v-for="item in type"
              :key="item.value"
              :label="item.label"
              :detect="item.value"
            />
          </el-select>
        </el-form-item>
        <el-form-item label="疑似病患">
          <el-select v-model="per" placeholder="请选择">
            <el-option
              v-for="item in person"
              :key="item.value"
              :label="item.label"
              :per="item.value"
            />
          </el-select>
        </el-form-item>
        <el-form-item label="上传图片">
          <el-upload
            action="#"
            list-type="picture-card"
            :auto-upload="false"
          >
            <i slot="default" class="el-icon-plus" />
            <div slot="file" slot-scope="{file}">
              <img
                class="el-upload-list__item-thumbnail"
                :src="file.url"
                alt=""
              >
              <span class="el-upload-list__item-actions">
                <span
                  class="el-upload-list__item-preview"
                  @click="handlePictureCardPreview(file)"
                >
                  <i class="el-icon-zoom-in" />
                </span>
                <span
                  v-if="!disabled"
                  class="el-upload-list__item-delete"
                  @click="handleDownload(file)"
                >
                  <i class="el-icon-download" />
                </span>
                <span
                  v-if="!disabled"
                  class="el-upload-list__item-delete"
                  @click="handleRemove(file)"
                >
                  <i class="el-icon-delete" />
                </span>
              </span>
            </div>
          </el-upload>
          <el-dialog :visible.sync="dialogVis">
            <img width="100%" :src="dialogImg" alt="">
          </el-dialog>
        </el-form-item>
      </el-form>
      <span slot="footer" class="dialog-footer">
        <el-button type="primary" @click="centerdialogFormVisible = false">提 交</el-button>
      </span>
    </el-dialog>
    <div class="list">
      <div>
        <p class="title"><img src="@/assets/imgs/patient.png" alt="">&nbsp;患者列表</p>
      </div>
      <div class="patient_box">
        <div v-for="(item,index) in patientList" :key="index" class="box">
          <div><img :src="`${item.avatar}`" alt=""></div>
          <div>
            <span>{{ item.name }} ></span>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import { getInfo, getPatient } from '@/api/user'
export default {
  data() {
    return {
      role: '',
      dialogFormVisible: false,
      dialogDetection: false,
      form: {
        name: '',
        number: '',
        mail: ''
      },
      formLabelWidth: '120px',
      centerdialogFormVisible: false,
      dialogImageUrl: '',
      dialogVisible: false,
      type: [{
        value: '选项1',
        label: '肺结核检查'
      }, {
        value: '选项2',
        label: '肺结节检查'
      }, {
        value: '选项5',
        label: '其他检查'
      }],
      person: [{
        value: '选项1',
        label: '张三'
      }, {
        value: '选项5',
        label: '李四'
      }],
      value: '',
      per: '',
      detect: '',
      dialogVis: false,
      dialogImg: '',
      disabled: false,
      info: '',
      patientList: ''
    }
  },
  created() {
    getInfo('TokenFromChenxin').then(res => {
      this.info = res.data
      console.log(this.info)
    }).catch(err => {
      console.log(err)
    })
    getPatient().then(res => {
      this.patientList = res.data.patientList
      console.log(this.patientList)
    }).catch(err => {
      console.log(err)
    })
  },
  methods: {
    handleRemove(file, fileList) {
      console.log(file, fileList)
    },
    handlePictureCardPreview(file) {
      this.dialogImageUrl = file.url
      this.dialogVisible = true
    }
  }
}
</script>
<style lang="scss" scoped>
.app-container{
  display:flex;
}
.card{
  display:flex;
  width:270px;
  height:380px;
  background-color: rgba(131, 122, 122, 0.1);
  margin-top: 180px;
  margin-left: 30px;
  border-radius: 20px;
  flex-direction: column;
  .title{
    color:#fff;
    font-size:16px;
    margin:17px 20px;
    img{
      width:20px;
      height:20px;
      vertical-align: sub;
    }
  }
  .pho{
    display:flex;
    justify-content: center;
    .photo{
      margin-top: 5px;
      img{
        width:100px;
        height:100px;
        border-radius: 11px;
      }
    }
  }
  .info{
    margin-top:-8px;
    .box{
      background-color: rgba(189, 181, 181, 0.2);
      background-size: cover;
      height:40px;
      display:flex;
      align-items: center;
      justify-content: space-between;
      margin-top: 20px;
      span{
        color:#fff;
        margin:auto 15px;
        img {
          width:14px;
          height:14px;
        }
      }
    }
  }
}
.func{
  display:flex;
  width:300px;
  height:380px;
  background-color: rgba(131, 122, 122, 0.1);
  margin-top: 180px;
  margin-left: 30px;
  border-radius: 20px;
  flex-direction: column;
  .title{
    color:#fff;
    font-size:16px;
    margin:17px 20px;
    img{
      width:20px;
      height:20px;
      vertical-align: sub;
    }
  }
  .add{
    background-color: rgba(189, 181, 181, 0.2);
    height:140px;
    display:flex;
    flex-wrap: wrap;
    align-items: center;
    justify-content: space-between;
    .text{
      margin: auto 20px;
      p{
        color:#fff;
        line-height: 0.7;
      }
    }
    .addimg{
      margin:auto 20px;
      img{
        width:60px;
        height:60px;
      }
    }
  }
}
.upload{
  margin-top:20px;
  background-color: rgba(189, 181, 181, 0.2);
  height:140px;
  display:flex;
  flex-wrap: wrap;
  align-items: center;
  justify-content: space-between;
  .text{
    margin: auto 20px;
    p{
      color:#fff;
      line-height: 0.7;
    }
  }
  .addimg{
    margin:auto 20px;
    img{
      width:60px;
      height:60px;
    }
  }
}
.list{
  display:flex;
  width:300px;
  height:380px;
  background-color: rgba(131, 122, 122, 0.1);
  margin-top: 180px;
  margin-left: 30px;
  border-radius: 20px;
  flex-direction: column;
  .title{
    color:#fff;
    font-size:16px;
    margin:17px 20px;
    img{
      width:20px;
      height:20px;
      vertical-align: sub;
    }
  }
  .patient_box{
    overflow-y: auto;
    /* 定义滚动条样式 */
  &::-webkit-scrollbar {
    width: 6px;
    height: 6px;
    background-color: rgba(195, 189, 189, 0.6);
  }
  /*定义滚动条轨道 内阴影+圆角*/
  &::-webkit-scrollbar-track {
    box-shadow: inset 0 0 0px rgba(240, 240, 240, .5);
    border-radius: 10px;
    background-color: rgba(240, 240, 240, .5);
  }
  /*定义滑块 内阴影+圆角*/
  &::-webkit-scrollbar-thumb {
    border-radius: 10px;
    box-shadow: inset 0 0 0px rgba(49, 48, 59, 0.5);
    background-color: rgba(49, 48, 59, 0.5);
  }

    .box{
      display:flex;
      justify-content: space-between;
      align-items: center;
      border: 1px rgb(123, 117, 117) solid;
      border-radius: 12px;
      margin: 12px 12px;
      div{
        margin:2px 10px;
      }
      img{
        width:55px;
        height:55px;
        border-radius: 8px;
      }
      span{
        color:#fff;
      }
    }
  }
}
</style>
