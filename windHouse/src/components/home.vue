<template>
  <div class="home">
    <div class="header">
      <div class="wrapper">
        <div class="chose_city">
          <a>广州<i class="icon fa fa-caret-down" aria-hidden="true"></i></a>
          <div class="separate"></div>
        </div>
        <div class="search">
          <input type="text" placeholder="请输入小区/商圈/地铁">
        </div>
      </div>
    </div>
    <div class="content">
      <banner class="banner"></banner>
      <div style="height:1000px">
        <span>{{clickType}}</span>
        <button class="tapTest">单击/双击</button>
      </div>
    </div>
  </div>
</template>

<script>
import banner from '@/components/banner';

export default {
  name: 'home',
  components: {
    banner,
  },
  data() {
    return {
      clickType: '尚未点击',
    };
  },
  mounted() {
    this.$nextTick(() => {
      console.log($('.tapTest'));
      console.log($('.tapTest').hasClass('tapTest'));
      console.log($('.tapTest').hasClass('tapTest22'));
      $('.tapTest').on('singleTap', () => {
        console.log('singleTap');
        console.log(this);
        this.clickType = '单击';
      });
      $('.tapTest').on('doubleTap', () => {
        console.log('doubleTap');
        this.clickType = '双击';
      });
    });
  },
};
</script>

<style scoped lang="less">
.header {
  position: fixed;
  z-index: 100;
  top: 0px;
  height: 50px;
  width: 100%;
  background: white;
  .wrapper {
    display: flex;
    width: 90%;
    height: 30px;
    margin: 10px auto;
    border-radius: 2px;
    background: #f8f8f8;
    .chose_city {
      flex: 1;
      padding: 5px 0 5px 5px;
      .icon {
        margin-left: 5px;
      }
      .separate {
        float: right;
        width: 1px;
        height: 20px;
        border: 1px;
        background: #d4c9c9;
      }
    }
    .search {
      flex: 4;
      display: table-cell;
      padding: 5px;
      input { 
        width: 95%;
        line-height: 20px;
        background: #f8f8f8;
        border: none;
        &::-webkit-input-placeholder{text-align: center;} 
      }
    }
  }
}

.content {
  width: 90%;
  height: 100%;
  overflow: auto;
  margin: 0 auto;
}

.banner {
  height: 80px;
  overflow: hidden;
}
</style>