<template>
  <div id='editor'>
    <nav>
      <ol>

        <li v-for='i in [0,1,2,3,4,5]'
          v-bind:class="{active: currentTab === i}"
          v-on:click="currentTab = i"
        >
          <svg class="icon"> 
            <use v-bind:xlink:href="`#icon-${icons[i]}`"></use>
          </svg>
        </li>

      </ol>
    </nav>
    <ol class="panes">
      <li v-bind:class="{active: currentTab === 0}">
        <ProfileEditor v-bind:profile='profile' />
      </li>
      <li v-bind:class="{active: currentTab === 1}">
        <h2>工作经历</h2>
        <el-form>
          <div class="container" v-for="(work, index) in workHistory">
            <el-form-item label="公司">
              <el-input v-model="work.company"></el-input>
            </el-form-item>
            <el-form-item label="工作内容">
              <el-input v-model="work.content"></el-input>
            </el-form-item>
            <i class="el-icon-circle-close" v-on:click = "removeWorkHistory(index)"></i>
          </div>
          <el-button type="primary" v-on:click = "addWorkHistory">添加经历</el-button>
        </el-form>
      </li>
      <li v-bind:class="{active: currentTab === 2}">
        <h2>学习经历</h2>
      </li>
      <li v-bind:class="{active: currentTab === 3}">
        <h2>项目经历</h2>
      </li>
      <li v-bind:class="{active: currentTab === 4}">
        <h2>获奖情况</h2>
      </li>
      <li v-bind:class="{active: currentTab === 5}">
        <h2>联系方式</h2>
      </li>
    </ol>
  </div>
</template>

<script>
  import ProfileEditor from './ProfileEditor'
  export default {
    components: { ProfileEditor },
    data() {
      return {
        currentTab: 0,
        icons: ['id', 'work', 'book', 'project', 'jiangbei', 'phone'],
        profile: {
          name: '',
          city: '',
          birth: ''
        },
        workHistory: [
          { company: '', content: '' }
        ]
      }
    },
    methods: {
      addWorkHistory() {
        this.workHistory.push({
          company: '',
          content: ''
        })
      },
      removeWorkHistory(index) {
        this.workHistory.splice(index, 1)
      }
    },
    created(){

    }
  }
</script>

<style lang="scss">
  #editor {
    min-height: 100px;
    display: flex;

    > nav {
      width: 80px;
      background: #000;

      > ol > li {
        padding: 16px 0;
        text-align: center;
        
        > .icon {
          width: 24px;
          height: 24px;
          fill: #fff;
        }  
        &.active {
          background: #fff;
          > .icon {
            fill: #000;
          }
        }
      } 
    }
  >  .panes {
      flex: 1;
      .container {
        position: relative;
        .el-icon-circle-close {
          position: absolute;
          right: 0;
          top: 12px;
          cursor: pointer;
        }
      }
    > li {
        display: none;
        padding: 32px;
        height: 100%;
        overflow: auto;
        &.active {
          display: block;
        }
      }
    }
  }
</style>
