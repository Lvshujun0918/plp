<template>
  <header class="header">
    <div class="header-content">
      <h1 
        @click="goHome"
        class="site-title">
        幻想漂流瓶
      </h1>
      <el-button 
        type="info" 
        icon="InfoFilled" 
        circle 
        @click="showIntroduction"
        class="info-button"
        v-if="showInfoButton"
      />
    </div>
  </header>
</template>

<script>
import { ref } from 'vue'
import { useRouter } from 'vue-router'

export default {
  name: 'HeaderComponent',
  props: {
    showInfoButton: {
      type: Boolean,
      default: true
    }
  },
  setup() {
    const router = useRouter()
    
    const showIntroduction = () => {
      // 在新窗口中打开网站说明页面
      window.open('/introduction', '_blank')
    }

    const goHome = () => {
      router.push('/')
    }

    return {
      showIntroduction,
      goHome
    }
  }
}
</script>

<style scoped>
.header {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  z-index: 1000;
  background: rgba(0, 0, 0, 0.3);
  backdrop-filter: blur(20px);
  -webkit-backdrop-filter: blur(20px);
  padding: 10px 10px;
  border-bottom: 1px solid rgba(255, 255, 255, 0.1);
}

.header-content {
  display: flex;
  justify-content: space-between;
  align-items: center;
  max-width: 1200px;
  margin: 0 auto;
}

.site-title {
  color: white;
  font-size: 1.5rem;
  font-weight: bold;
  cursor: pointer;
}

.info-button {
  background: rgba(255, 255, 255, 0.2);
  border: none;
}
</style>