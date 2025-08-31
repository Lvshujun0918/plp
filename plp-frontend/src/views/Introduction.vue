<template>
  <div class="introduction-container">
    <HeaderComponent :show-info-button="false" />
    <main class="introduction-main">
      <div class="content-wrapper">
        <div class="markdown-content" v-html="renderedContent"></div>
      </div>
    </main>
    <FooterComponent />
  </div>
</template>

<script>
import { ref, computed } from 'vue'
import HeaderComponent from '../components/Header.vue'
import FooterComponent from '../components/Footer.vue'
import { marked } from 'marked'

export default {
  name: 'Introduction',
  components: {
    HeaderComponent,
    FooterComponent
  },
  setup() {
    // 网站说明内容（Markdown格式）
    const introductionContent = ref(`
# 网站说明

---

匿名海洋 漂浮着千万种心事——

掷出你的天马行空

捞起陌生星球的回响。

没有账号，不留痕迹，只有此刻的浪花。

---

## 漂流瓶投放须知

### 总述

天马行空的人可以盯着桌上的物品幻想一个下午。
  
在这个网站上，幻想爱好者将发布自己的幻想：可以是"空想"，无须以现实为根基，仅用文字编织幻想的乐章；也可以是"联想"，赋予枯燥无味的现实图景名为"幻想"的生命力。

将幻想装入漂流瓶扔出后，经漂流瓶管理局审批通过后，漂流瓶将进入匿名海洋。

其他从匿名海洋中拾起漂流瓶的人可以共同编辑这个幻想。

### 漂流瓶管理局的审批规则

#### 通用规则：

所有投放的内容均应属于"幻想"的范畴，该范畴最终解释权属于漂流瓶管理局

<font color=red> 每日至多仅可投放一个漂流瓶 </font>

禁止投放色情、暴力、涉政等敏感内容

禁止投放具有社会争议性的内容

禁止投放任何可能引起他人不适的内容，例如某些性暗示和精神污染内容

禁止投放任何意义不明的内容，包括但不限于加密的文本和图片

禁止投放各种奇怪的链接，包括但不限于小程序，二维码，文字跳转等形式，包括但不限于恶意网页，链接内容与描述不符，任何广告，比赛，问卷收集表等

#### 补充幻想规则：

补充的幻想应与原幻想自洽

补充的幻想应尊重原幻想的表达意图

用户不能修改已存在幻想的图片

漂流瓶管理局将审查对幻想的补充

#### 回应规则：

回应的内容将经过漂流瓶管理局审查

请对漂流瓶进行友善的回应！

#### 举报须知：

请通过页面下方邮箱举报，邮件中请附上漂流瓶id或评论id，以及相关证据截图！

也可以在漂流瓶的回应区写下举报回应，漂流瓶管理局能看到的！

---

## 设定说明

#### 幻想载体说明：牛皮纸（普通的纸，随心畅写，他人可补充幻想的内容） 、永恒纸（扔出后内容不可再补充，他人仅可查阅、回应）

#### "空想"说明：纯粹的幻想

"空想"允许用户发布不超过4000字的内容，不包含图片

"空想"没有其余特殊要求，自由发挥吧~

#### "联想"说明：重塑现实的幻想

"联想"允许用户发布不超过8000字的内容，必须包含图片

"联想"的文本内容必须和图片的内容有强相关性
`)
    
    // 渲染Markdown内容
    const renderedContent = computed(() => {
      return marked(introductionContent.value)
    })
    
    return {
      renderedContent
    }
  }
}
</script>

<style scoped>
.introduction-container {
  min-height: 100vh;
  display: flex;
  flex-direction: column;
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
  padding-top: 85px; /* Header 高度 */
}

.introduction-main {
  flex: 1;
  padding: 0;
  width: 100%;
  display: flex;
  justify-content: center;
  align-items: flex-start;
}

.content-wrapper {
  background: rgba(255, 255, 255, 0.95);
  backdrop-filter: blur(10px);
  border-radius: 0; /* 设置为直角矩形 */
  padding: 30px;
  box-shadow: 0 8px 32px rgba(0, 0, 0, 0.1);
  width: 100%;
  max-width: 800px;
  margin-top: 20px;
  max-height: calc(100vh - 210px);
  overflow-y: scroll;
  margin: 0 auto;
}

.markdown-content {
  color: #333;
  line-height: 2.1; /* 增加行高 */
  font-size: 16px; /* 设置基础字体大小 */
}

.markdown-content h1,
.markdown-content h2,
.markdown-content h3 {
  color: #2c3e50;
  margin-top: 30px; /* 增加上边距 */
  margin-bottom: 20px; /* 增加下边距 */
  font-weight: 600;
  line-height: 1.3;
}

.markdown-content h1 {
  font-size: 28px;
  border-bottom: 1px solid #eaecef;
  padding-bottom: 10px;
}

.markdown-content h2 {
  font-size: 24px;
  border-bottom: 1px solid #eaecef;
  padding-bottom: 8px;
}

.markdown-content h3 {
  font-size: 20px;
}

.markdown-content p {
  margin-bottom: 30px; /* 增加段落间距 */
  font-size: 16px;
}

.markdown-content ul,
.markdown-content ol {
  padding-left: 30px; /* 增加列表缩进 */
  margin-bottom: 20px; /* 增加列表间距 */
}

.markdown-content li {
  margin-bottom: 10px; /* 增加列表项间距 */
}

.markdown-content a {
  color: #42b983;
  text-decoration: none;
}

.markdown-content a:hover {
  text-decoration: underline;
}

.markdown-content code {
  background-color: #f6f8fa;
  padding: 4px 6px; /* 增加内边距 */
  border-radius: 4px;
  font-family: monospace;
  font-size: 14px;
}

.markdown-content pre {
  background-color: #f6f8fa;
  padding: 16px; /* 增加内边距 */
  border-radius: 6px;
  overflow-x: auto;
  margin-bottom: 20px; /* 增加底部间距 */
}

.markdown-content pre code {
  background: none;
  padding: 0;
}
</style>