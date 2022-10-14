<template>
  <div class="app-container">
    <div class="card">
      <div>
        <p class="title"><img src="@/assets/imgs/doctor.png" alt="">&nbsp;医生</p>
      </div>
      <div class="pho">
        <p class="photo"><img src="@/assets/imgs/bg13.jpg" alt=""></p>
      </div>
      <div class="info">
        <div class="box">
          <span>Account</span>
          <span>chenxin <img src="@/assets/imgs/user.png" alt=""></span>
        </div>
        <div class="box">
          <span>Mail</span>
          <span>miao <img src="@/assets/imgs/mail.png" alt=""></span>
        </div>
        <div class="box">
          <span>Phone</span>
          <span>miao <img src="@/assets/imgs/phone.png" alt=""></span>
        </div>
      </div>
    </div>
    <div class="func">
      <div>
        <p class="title"><img src="@/assets/imgs/doctor.png" alt="">&nbsp;核心功能</p>
      </div>
      <div class="add">
        <div class="text">
          <p>添加</p>
          <p>疑似病患</p>
        </div>
        <div class="addimg"></div>
      </div>
      <div class="upload"></div>
    </div>
  </div>
</template>

<script>
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
    background-color: red;
    height:140px;
    display:flex;
    flex-wrap: wrap;
    align-items: center;
    .text{
      p{
        color:#fff;
        line-height: 0.7;
      }
    }
  }
}
</style>
