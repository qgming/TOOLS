<template>
  <div class="about">
    <div class="topAbout">
      <RouterLink class="backHome" to="/">返回首页</RouterLink>
      <div class="aboutName">关于</div>
      <div class="aboutTop">
        <img class="aboutLogo" src="../assets/images/polarlogo.png" alt="logo" srcset="">
        <p class="webName">极点智能体<br>Extreme Ai Agent</p>
        <p class="version">V0.3.7(22)</p>
        <p class="aboutEmail">qgming@qq.com</p>
        <p class="aboutBottom">©️极点维度<br>Extreme Dimension</p>
        <p class="otherName">由<a href="https://siliconflow.cn/zh-cn/"
            target="_blank">硅基流动</a>提供默认大模型支持<br>通义千问（Qwen2-7B-Instruct）</p>
      </div>

    </div>
  </div>
</template>

<script>

</script>

<style scoped>
.about {
  display: flex;
  flex-direction: column;
  align-items: center;
}

.topAbout {
  width: 600px;
  display: flex;
  flex-direction: column;
  user-select: none;
}

.backHome {
  width: 100px;
  color: white;
  text-align: center;
  text-decoration: none;
  padding: 4px;
  background-color: skyblue;
  border-radius: 9px;
  margin-top: 20px;
  margin-bottom: 5px;
}

.backHome:hover {
  background-color: rgb(100, 200, 240);
}

.aboutName {
  font-size: 30px;
  font-weight: 600;

}

.webName {
  font-size: 30px;
  font-weight: 600;
  text-align: center;
}

.aboutTop {
  width: 600px;
  margin-top: 10px;
  padding: 10px;
  border-radius: 12px;
  background-color: #f9f9f9;
  border: 1px solid #eaeaea;
  /* border: 1px solid rgb(135, 206, 235); */
  display: flex;
  flex-direction: column;
  align-items: center;
}

.aboutLogo {
  width: 90px;
  height: 90px;
  margin: 10px;
  border-radius: 12px;
}

.version {
  font-size: 16px;
  font-weight: 600;
  color: rgb(135, 206, 235);
}

.aboutEmail {
  margin-top: 50px;
  padding: 5px 10px;
  background-color: #ffffff;
  border: 1px solid #eaeaea;
  border-radius: 9px;
}

.aboutBottom {
  margin-top: 30px;
  text-align: center;
}

.otherName {
  margin-top: 10px;
  font-size: 12px;
}


@media screen and (max-width: 768px) {
  .topAbout {
    width: 360px;
  }

  .aboutTop {
    width: 360px;
  }

}
</style>
