<template>
  <div class="all">
    <div class="upBox">
      <div>
        <RouterLink class="toSetting" to="/setting">设置</RouterLink>
      </div>
      <div class="searchBox">
        <img class="searchImg" src="../assets/images/polarlogo2.png" alt="">
        <input type="text" class="searchInput">
      </div>
    </div>
    <div class="home">
      <el-affix :offset="100">
        <div class="pageLeft">
          <ol>
            <li v-for="(item, index) in sections" :key="index">
              <a class="option" :href="'#' + item.id" @click="setActiveSection(index)" :ref="'section' + index">{{
                item.name }}</a>
            </li>
          </ol>
        </div>
      </el-affix>
      <div class="pageRight">
        <div class="oneTool" v-for="(toolname, index) in sections" :key="index">
          <div class="toolName" :id="toolname.name">{{ toolname.name }}</div>
          <div class="anyCard">
            <div class="toolCard" @click="openTools(tool)" v-for="tool in getToolCards(index + 1)" :key="tool.id">
              <div class="logoBox">
                <img class="toolLogo" :src="tool.logo" alt="logo">
              </div>
              <div class="cardText">
                <p class="cardName">{{ tool.name }}</p>
                <p class="cardMore">{{ tool.more }}</p>
              </div>
            </div>
          </div>
        </div>
      </div>
      <div class="pageMine">
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      sections: [
        { id: '编辑精选', name: '编辑精选' },
        { id: '新媒体', name: '新媒体' },
        { id: '职场办公', name: '职场办公' },
        { id: '学习助手', name: '学习助手' },
        { id: '生活娱乐', name: '生活娱乐' },
        { id: '极客', name: '极客' },
        { id: '实验室', name: '实验室' },
      ],
      toolCards: [
        // 编辑精选
        [
          { id: 1, logo: "../images/biganzi.png", name: "公文笔杆子", more: '提升效率，驾驭文书之道', prompt: '../prompt/002/gongwen.txt' },
          { id: 1, logo: '../images/artist.png', name: "绘画大师", more: '根据你的要求，绘画大师帮你生成适合文生图模型的"咒语"。', prompt: '../prompt/005/drawprompt.txt' },
          { id: 4, logo: "../images/wechat.png", name: "公众号文章", more: '公众号写作助理，侧重于产品分享文章', prompt: '../prompt/001/gongzhonghao.txt' },
          { id: 5, logo: '../images/fanyi.png', name: "翻译专家", more: '精通多国语言，使用方法：输入需要翻译的内容，并在末尾加（翻译成日语）来使用', prompt: '../prompt/002/fanyi2.txt' },
          { id: 3, logo: "../images/xiaohongshu.png", name: "小红书生成器", more: '小红书爆款生成器', prompt: '../prompt/001/xiaohongshu.txt' },

        ],
        // 新媒体001
        [
          { id: 1, logo: '../images/jizhe.png', name: "新闻记者", more: '以记者的身份写报道', prompt: '../prompt/001/xinwenjizhe.txt' },
          { id: 2, logo: '../images/xiaohongshu.png', name: "小红书生成器", more: '小红书爆款生成器', prompt: '../prompt/001/xiaohongshu.txt' },
          { id: 3, logo: '../images/wechat.png', name: "公众号文章", more: '公众号写作助理，侧重用产品分享文章', prompt: '../prompt/001/gongzhonghao.txt' },
          { id: 4, logo: '../images/weibo.png', name: "微博文案", more: '这是这个卡片的介绍', prompt: '../prompt/001/weibo.txt' },
          { id: 5, logo: '../images/douyin.png', name: "抖音脚本", more: '根据主题生成爆款短视频脚本', prompt: '../prompt/001/douyin.txt' },
          { id: 6, logo: '../images/jizhe.png', name: "资讯自媒体", more: '一个根据新闻快速生成自媒体文章的AI', prompt: '../prompt/001/zimeiti.txt' },

        ],
        // 职场办公002
        [
          { id: 1, logo: '../images/biganzi.png', name: "公文笔杆子", more: '提升效率，驾驭文书之道', prompt: '../prompt/002/gongwen.txt' },
          { id: 2, logo: '../images/fanyi.png', name: "中英互译", more: '一键中英互译，直译意译，样样精通', prompt: '../prompt/002/fanyi.txt' },
          { id: 3, logo: '../images/ppt.png', name: "PPT助手", more: '让你的PPT既有Power，又有Point', prompt: '../prompt/002/ppt.txt' },
          { id: 4, logo: '../images/zhoubao.png', name: "周报生成器", more: '根据日常工作内容，提取要点并适当扩充，以生成周报。', prompt: '../prompt/002/zhoubao.txt' },
          { id: 5, logo: '../images/fanyi.png', name: "翻译专家", more: '输入需要翻译的内容，并在末尾加（翻译成日语）来使用', prompt: '../prompt/002/fanyi2.txt' },
          { id: 6, logo: '../images/aixin.png', name: "一线故事", more: '暖心一线故事', prompt: '../prompt/002/yixiangushi.txt' },
        ],
        // 学习助手003
        [
          { id: 1, logo: '../images/xielunwen.png', name: "论文助写", more: '像教授一样写论文', prompt: '../prompt/003/lunwenxiezuo.txt' },
          { id: 2, logo: '../images/gailunwen.png', name: "论文改写", more: '文章降重，降低AI率', prompt: '../prompt/003/lunwengaixie.txt' },
          { id: 3, logo: '../images/zhoubao.png', name: "学习任何东西", more: '帮你学习任何东西', prompt: '../prompt/003/xuexirenhe.txt' },
          { id: 4, logo: '../images/feiman.png', name: "费曼学习法", more: '像费曼一样学习', prompt: '../prompt/003/feiman.txt' },
          { id: 5, logo: '../images/think.png', name: "深度思考", more: '多角度深度思考，发现问题，解决问题', prompt: '../prompt/003/sikao.txt' },
          { id: 6, logo: '../images/baike.png', name: "极点百科", more: '帮你了解任何东西', prompt: '../prompt/003/baike.txt' },
          { id: 7, logo: '../images/teacher.png', name: "英文阅读讲师", more: '帮你学习英语阅读', prompt: '../prompt/003/xueyingyu.txt' },

        ],
        // 生活娱乐004
        [
          { id: 1, logo: '../images/lvxing.png', name: "旅行规划师", more: '保姆级旅游规划师，衣食住行全包揽', prompt: '../prompt/004/lvxingguihua.txt' },
          { id: 2, logo: '../images/xiaohongshu.png', name: "婚姻法专家", more: '婚姻法专家', prompt: '../prompt/004/huiyinfa.txt' },
          { id: 3, logo: '../images/taluo.png', name: "塔罗牌", more: '来玩塔罗牌（仅供娱乐）', prompt: '../prompt/004/taluo.txt' },
          { id: 4, logo: '../images/chengzhangjiaolian.png', name: "成长教练", more: '给出专业的人生建议[需连续对话]', prompt: '../prompt/004/chengzhangjiaolian.txt' },
          { id: 5, logo: '../images/taluo.png', name: "六爻占卜", more: '赛博六爻占卜（仅供娱乐）', prompt: '../prompt/004/6yao.txt' },

        ],
        // 极客005
        [
          { id: 1, logo: '../images/ppt.png', name: "提示词工程师", more: '根据你的要求，提示词工程师帮你生成提示词。', prompt: '../prompt/005/prompt.txt' },
          { id: 2, logo: '../images/song.png', name: "作词家", more: '根据你的要求，作词家帮你生成适合Suno AI的歌词。', prompt: '../prompt/005/sunoai.txt' },
          { id: 3, logo: '../images/artist.png', name: "绘画大师", more: '根据你的要求，绘画大师帮你生成适合文生图模型的"咒语"。', prompt: '../prompt/005/drawprompt.txt' },
          { id: 4, logo: '../images/ppt.png', name: "问题解决专家", more: '根据引导，逐步解决你的问题。', prompt: '../prompt/005/question.txt' },

        ],
        // 实验室006
        [
          { id: 1, logo: '../images/polarlogo.png', name: "空白智能体", more: '无提示词', prompt: '' },
          { id: 2, logo: '../images/ai.png', name: "规则怪谈游戏", more: '提示词测试1', prompt: '../prompt/006/test.txt' },
          { id: 3, logo: '../images/ai.png', name: "文明游戏", more: '提示词测试2', prompt: '../prompt/006/test2.txt' },
          { id: 4, logo: '../images/ai.png', name: "绘画大师", more: '支持图片预览', prompt: '../prompt/006/test3.txt' },
        ],
      ],
    };
  },
  methods: {
    getToolCards(categoryIndex) {
      return this.toolCards[categoryIndex - 1] || [];
    },
    //进入工具组件，传递初始提示词
    openTools(a) {
      this.$store.dispatch('setTool', a); // 使用 Vuex 传递数据
      this.$router.push({
        path: '/tool'
      });
    },
  },
  mounted() {

  },
  beforeDestroy() {

  },
};
</script>

<style scoped>
.all {
  margin-top: 20px;
  display: flex;
  flex-direction: column;
  align-items: center;
}

.upBox {
  display: flex;
  align-items: center;
  width: 1000px;
}

.toSetting {
  background-color: #f9f9f9;
  border: 1px solid #eaeaea;
  font-size: 16px;
  margin: 30px;
  padding: 10px 30px;
  color: black;
  text-decoration: none;
  border-radius: 9px;
  user-select: none;
}

.toSetting:hover {
  color: white;
  background-color: skyblue;
}

.searchBox {
  display: flex;
  background-color: #f9f9f9;
  border: 1px solid #eaeaea;
  border-radius: 12px;
  /* width: 1000px; */
  height: 50px;
}

.searchBox:hover {
  border: 1px solid skyblue;
}

.searchImg {
  padding: 5px;
  height: 50px;
  width: 50px;
}

.searchInput {
  font-size: large;
  color: #a3a3a3;
  width: 760px;
  height: 50px;
  outline: none;
  border: none;
  background-color: rgba(249, 249, 249, 0);
}

.home {
  display: flex;
}

.pageLeft {
  width: 120px;
}

.pageLeft ol {
  padding: 5px;
}

li {
  margin-top: 15px;
  text-align: right;
  text-decoration: none;
}

.option {
  color: grey;
  font-size: larger;
  text-decoration: none;
  padding: 5px 10px;
  user-select: none;
}

.option:hover {
  color: white;
  background-color: skyblue;
  border-radius: 9px;
  transition: transform 300ms ease-out;
}

/* AI工具卡片 */
.pageRight {
  margin: 10px 20px;
}

.toolName {
  font-size: 20px;
  margin: 5px 0;
  color: #b9b9b9;
  user-select: none;
}

.anyCard {
  display: flex;
  width: 816px;
  flex-wrap: wrap;
}

.toolCard {
  display: flex;
  align-items: center;
  width: 260px;
  height: 100px;
  background-color: #f9f9f9;
  border: 1px solid #eaeaea;
  border-radius: 12px;
  margin: 6px;
  padding: 16px 8px;
  user-select: none;
}

.toolCard:hover {
  border: 1px solid rgb(135, 206, 235);
  box-shadow: rgba(135, 206, 235, 0.05) 0 6px 24px 0, rgba(0, 0, 0, 0.08) 0 0 0 1px;
  color: skyblue;
  transition: transform 300ms ease-out;
  /* 调整过渡时间和缓动函数 */
  transform: scale(1.03);
}

.toolLogo {
  width: 50px;
  height: 50px;
  border-radius: 12px;
}

.cardText {
  width: 190px;
  margin-left: 5px;
}

.cardName {
  font-size: larger;
  font-weight: 600;
}

.cardMore {
  color: #a3a3a3;
  max-height: 50px;
  margin: 0;
  padding: 0;
  overflow: hidden;
  text-overflow: ellipsis;
}

@media screen and (max-width: 768px) {
  .upBox {
    display: none;
  }

  .pageLeft {
    display: none;
  }

  .pageRight {
    margin: 0;
  }

  .anyCard {
    width: 360px;
  }

  .toolCard {
    width: 170px;
    height: 80px;
    margin: 5px;
    padding: 8px 4px;
  }

  .cardText {
    width: 140px;
    margin-left: 5px;
  }

  .cardName {
    font-weight: 500;
    overflow: hidden;
    max-height: 30px;
    text-overflow: ellipsis;
  }


}
</style>
