<template>
  <div class="dashboard">
    <div class="nav">
      <ul class="ul_top">
        <li @mouseenter="mouseover(1)"><p>肺结核</p></li>
        <li @mouseenter="mouseover(2)"><p>肺结节</p></li>
        <li @mouseenter="mouseover(3)"><p>喉咙</p></li>
        <li @mouseenter="mouseover(4)"><p>新冠</p></li>
      </ul>
    </div>
    <div class="content">
      <ul class="ul_rt">
        <li v-show="tag==1">
          <img src="../../assets/imgs/index1.png" alt="">
        </li>
        <li v-show="tag==2">
          <img src="../../assets/imgs/index2.png" alt="">
        </li>
        <li v-show="tag==3">
          <img src="../../assets/imgs/index3.png" alt="">
        </li>
        <li v-show="tag==4">
          <img src="../../assets/imgs/index4.png" alt="">
        </li>
      </ul>
    </div>
    <div class="card">
      <div class="dark-select">
        <el-select v-model="form.id" :popper-append-to-body="false" class="sel">
          <el-option v-for="item in options" :key="item.value" :label="item.label" :value="item.value" />
        </el-select>
      </div>
      <div class="cont">
        <div v-if="form.id==1" class="content-box">
          <el-button type="goon" size="small" style="width:40%;">{{ context[form.id-1].title[0] }}</el-button>
          <p class="word">{{ context[form.id-1].text[0] }}
          </p>
          <el-button type="goon" size="small" style="width:40%;">{{ context[form.id-1].title[1] }}</el-button>
          <p class="word">{{ context[form.id-1].text[1] }}
          </p>
          <el-button type="goon" size="small" style="width:40%;">{{ context[form.id-1].title[2] }}</el-button>
          <p class="word">{{ context[form.id-1].text[2] }}
          </p>
          <el-button type="goon" size="small" style="width:40%;">{{ context[form.id-1].title[3] }}</el-button>
          <p class="word">{{ context[form.id-1].text[3] }}
          </p>
        </div>
        <div v-else-if="form.id==2" class="content-box">
          <el-button type="goon" size="small" style="width:50%;">{{ context[form.id-1].title[0] }}</el-button>
          <p class="word">{{ context[form.id-1].text[0] }}
          </p>
          <el-button type="goon" size="small" style="width:50%;">{{ context[form.id-1].title[1] }}</el-button>
          <p class="word">{{ context[form.id-1].text[1] }}
          </p>
          <el-button type="goon" size="small" style="width:50%;">{{ context[form.id-1].title[2] }}</el-button>
          <p class="word">{{ context[form.id-1].text[2] }}
          </p>
        </div>
        <div v-else-if="form.id==3" class="content-box">
          <el-button type="goon" size="small" style="width:55%;">{{ context[form.id-1].title[0] }}</el-button>
          <p class="word">{{ context[form.id-1].text[0] }}
          </p>
          <el-button type="goon" size="small" style="width:55%;">{{ context[form.id-1].title[1] }}</el-button>
          <p class="word">{{ context[form.id-1].text[1] }}
          </p>
          <el-button type="goon" size="small" style="width:55%;">{{ context[form.id-1].title[2] }}</el-button>
          <p class="word">{{ context[form.id-1].text[2] }}
          </p>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import { mapGetters } from 'vuex'

export default {
  name: 'Dashboard',
  data() {
    return {
      tag: 1,
      form: {
        id: 1
      },
      options: [{
        value: 1,
        label: '肺结核是什么'
      }, {
        value: 2,
        label: '肺结核之痛'
      }, {
        value: 3,
        label: '诊断市场分析'
      }],
      context: [{
        value: 1,
        title: ['定义', '死亡率高', '传染能力强', '诊断流程待优化'],
        text: ['结核病是由结核分枝杆菌感染引起的一种慢性传染病，可累及全身各个脏器。其中，肺部是感染结核菌的最主要脏器，称为肺结核。',
          '肺结核(TB)是世界上第二大死亡原因，在传染病中排名第一，超过艾滋病。',
          '结核病是呼吸道传染病，主要通过飞沫传播。感染后终身携带病菌，约有10%-15%的感染者会在一定条件下发展为活动性结核病，成为新患者并继续传染给其他人。',
          '传统肺结核诊断方式花费高、时间长，病患的经济、心理压力大，且其诊疗流程中复杂、反复。']
      }, {
        value: 2,
        title: ['医疗资源分布不均', '价格高昂', '检测结果不确定性'],
        text: ['全国三甲医院数量仅1580家，中西部及农村等肺结核发病率较高的地区肺结核的接诊数可达每年1000人以上，医疗资源分布不均。',
          '肺结核单次检验费可达2000元以上，总确诊费用可占深圳单月人均收入60%，且病愈三年内仍需多次检测，患者经济压力大。',
          '医生判读肺结核痰涂片需观察300个视野，至少需要5-10分钟，每个工作日，一名镜检人员的玻片阅读量为15-20张，检测方式难以应对较大的检测需求。']
      }, {
        value: 3,
        title: ['医疗机构诊断能力不均衡', '检测方式有待改进', '患者空间分布不均', '患者经济压力极大'],
        text: ['三甲医院拥有较强的结核病诊断检测能力，但检测需求大，存在医生及检测设备超负荷工作问题，并且诊断效率与准确率不高。',
          '肺结核痰标本检测方法用时最短需要5-10分钟的时间，每个工作日，一名镜检人员的玻片阅读量不应超过25张，因此现行检测方式难以应对较大的检测需求。',
          '我国肺结核发病率为55.5491/100000，即每10万中有56人发病。中西部地区及农村地区肺结核发病率较高且三甲医院数量较少仅600-900家，可见诊疗压力极大。',
          '肺结核痰标本单次检验需要2000元以上，再加上附加费用，预估检测总费用将达到4000元，占深圳单月人均收入60%，需要反复检测，患者家庭面临较大的经济压力。']
      }]
    }
  },
  computed: {
    ...mapGetters([
      'name'
    ])
  },
  created() {
    this.form.id = this.options[0].value
  },
  methods: {
    mouseover(d) {
      this.tag = d
    }
  }
}
</script>

<style lang="scss" scoped>
.dashboard {
  display: flex;
}
.nav {
  margin-top:230px;
  margin-left: 0px;
  background-color:rgba(1,1,1,0.2);
  height:200px;
  width:210px;
  .ul_top {
    li {
      list-style: none;
      width:130px;
      text-align: center;
      p {
        color: #fff;
        font-weight: 200;
        font-size: 17px;
        cursor: pointer;
        line-height: 30px;
        text-align: center;
      }
    }
    p:hover {
      font-weight: 500;
      opacity: 0.8;
      font-size: 21px;
    }
  }
}
.content {
  .ul_rt {
    li {
      list-style: none;
      img {
        width:820px;
        //margin:-260px 140px;
        margin:100px 10px 100px -13px;
      }
    }
  }
}
.card {
  width:300px;
  height:auto;
  background-color: rgba(228, 226, 226, 0.2);
  .dark-select {
    margin-top: 50px;
    // 修改input默认值颜色 兼容其它主流浏览器
    ::v-deep input::-webkit-input-placeholder {
        color: rgba(255, 255, 255, 0.50);
    }
    ::v-deep input::-moz-input-placeholder {
        color: rgba(255, 255, 255, 0.50);
    }
    ::v-deep input::-ms-input-placeholder {
        color: rgba(255, 255, 255, 0.50);
    }
    // input框
    ::v-deep .el-select,
    ::v-deep .el-input,
    ::v-deep .el-input__inner {
        background-color: rgba(255, 255, 255, 0.04);
        color: rgba(255, 255, 255, 0.95);
        border: none; // 去掉边框
        // border-color: #XXXXXX // 默认边框的颜色
        text-align: left;
        border-radius: 4px;
    }

    // 选中时边框颜色
    // ::v-deep .el-input__inner:focus{
    //     border-color: #XXXXXX;
    // }

    // 鼠标悬浮时 input框颜色
    ::v-deep .el-input__inner:hover{
        background-color: rgba(255, 255, 255, 0.12);
    }

    // input框 右侧的箭头
    ::v-deep .el-select .el-input .el-select__caret {
        color: rgba(255, 255, 255, 0.50);
    }

    // option选项 上面的箭头
    ::v-deep .el-popper[x-placement^="bottom"] .popper__arrow::after {
        border-bottom-color: rgba(43, 45, 55, 0.80);
        z-index: 9999;
    }
    ::v-deep .popper__arrow {
        border: none;
    }
    // option选项 最外层
    ::v-deep .el-select-dropdown {
        border: none !important;
        background: rgba(40, 48, 88, 0.8) !important;
        z-index: 9999;
    }
    // option选项 文字样式
    ::v-deep .el-select-dropdown__item {
        color: rgba(255, 255, 255, 0.50) !important;
        z-index: 9999;
    }
    ::v-deep .el-select-dropdown__item.selected span{
        color: rgba(255, 255, 255, 0.80) !important;
        z-index: 9999;
    }
    // 移入option选项 样式调整
    ::v-deep .el-select-dropdown__item.hover{
        background-color: rgba(255, 255, 255, 0.06);
        color: rgba(255, 255, 255, 0.80) !important;
        z-index: 9999;
    }

	// 下拉框垂直滚动条宽度
    ::v-deep .el-scrollbar__bar.is-vertical {
         width: 10px;
         top: 2px;
     }
    // 下拉框最大高度
     ::v-deep .el-select-dropdown__wrap {
         max-height: 200px;
     }
     .sel {
      margin-left: 50px;
     }
  }
}
.cont {
  margin-top:30px;
  min-height: calc(100vh - 50px);
  .content-box {
    width:300px;
    height:400px;
    .el-button--goon {
      color: #FFF;
      background-color: #132c61 !important;
      border-color: #132c61;
    }
    .word {
      color:#fff;
      white-space: normal;
      font-size: 15px;
      font-weight: 400;
      line-height: 1.5;
      margin:10px 30px;
      text-align: justify;
      text-indent:2em;
    }
  }
}
</style>
