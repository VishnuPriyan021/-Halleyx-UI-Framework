<template>
  <div class="common-layout">
    <el-container>
      <el-aside width="200px">
        <section class="title">
          <router-link to="/"
            ><img
              src="./assets/img/Halleyx-Logo-Line-Dark.png"
              alt=""
              srcset=""
          /></router-link>
        </section>
        <nav class="side-nav">
          <router-link to="/tree">Tree</router-link>
          <router-link to="/badge">Badge</router-link>
          <router-link to="/dragdrop">DragDrop</router-link>
          <router-link to="/accordion">Accordion</router-link>
          <router-link to="/timeline">Timeline</router-link>
          <router-link to="/import">Import</router-link>
          <router-link to="/search">Search</router-link>
          <router-link to="/cards">Cards</router-link>
          <router-link to="/errorpage">ErrorPage</router-link>
          <router-link to="/layout">Layout</router-link>
          <router-link to="/breadcrumb">Breadcrumb</router-link>
          <router-link to="/sidebar">Sidebar</router-link>
          <router-link to="/input">Input</router-link>
          <router-link to="/input">Input</router-link>
          <router-link to="/input">Input</router-link>
          <router-link to="/input">Input</router-link>
          <router-link to="/input">Input</router-link>
          <router-link to="/input">Input</router-link>
          <router-link to="/input">Input</router-link>
          <router-link to="/input">Input</router-link>
          <router-link to="/input">Input</router-link>
          <router-link to="/input">Input</router-link>
          <router-link to="/input">Input</router-link>
        </nav>
      </el-aside>
      <el-container>
        <el-header class="header">
          <div class="search-bar">
            <el-input
              v-model="search"
              class="w-50 m-2"
              placeholder="Type something"
              clearable
            >
              <template #prefix>
                <el-icon class="el-input__icon"><search /></el-icon>
              </template>
            </el-input>
          </div>
        </el-header>
        <el-main>
          <router-view />
        </el-main>
      </el-container>
    </el-container>
  </div>
</template>

<script>
import { Search } from '@element-plus/icons-vue'
export default {
  name: 'App',
  components: {
    Search
  },
  data () {
    return {
      search: ''
    }
  }
}
</script>

<!-- @import "./assets/icon-style.css"; -->
<style lang="scss">
@import "./assets/styles/variables.scss";
body {
  margin: 0;
}
#app {
  // font-family: OpenSans;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #565553;
  aside {
    position:fixed;
    background: #fff;
    color: #969393;
    overflow: hidden;
    border-right: 1px solid #f0eeec;
    .title {
      height: 60px;
      box-shadow: 0 1px 15px -12px #565553;
      display: flex;
      align-items: center;
      justify-content: center;
      img {
        width: 150px;
      }
    }
    .side-nav {
      color: #565553;
      text-align: left;
      height: 91%;
      display: flex;
      overflow: auto;
      flex-wrap: wrap;
      a {
        font-size: 12px;
        width: 90%;
        text-decoration: none;
        color: #565553;
        &:hover {
          color: #f6991d;
          border-radius: 2px;
        }

        &.router-link-exact-active {
          color: #f6991d;
        }
      }
    }
  }
}
//   .header,
//   .el-header {
//     display: flex;
//     border-bottom: 1px solid #d4d4d4;
//     padding: 10px 10px;
//     align-items: center;
//     .search-bar {
//       width: 250px;
//       margin-left: auto;
//     }
//   }
//   .common-layout {
//     height: auto;
//     .el-container {
//       height: 100vh;
//       width: 100vw;
//     }
//   }
// }
// ::-webkit-scrollbar {
//   width: 6px;
//   height: 6px;
// }
// ::-webkit-scrollbar-track {
//   background-color: $secondary-color;
//   border-radius: 10px;
// }
// ::-webkit-scrollbar-thumb {
//   background: $primary-color;
//   border-radius: 10px;
// }
// ::-webkit-scrollbar-thumb:hover {
//   background: $primary-color;
// }
// .feature {
//   box-sizing: border-box;
// }
// .feature-title {
//   color: #606266;
// }
// .feature-content {
//   font-size: 0.875rem;
//   line-height: 1.25rem;
//   code {
//     margin: 0;
//     border-radius: 4px;
//     padding: 0.15rem 0.5rem;
//     color: #303133;
//     background-color: #f5f7fa;
//   }
// }
// .example-content {
//   border: 1px solid #e7e7e7;
//   border-radius: 3px;
//   .example-showcase {
//     padding: 1.5rem;
//     margin: 0.5px;
//     border-radius: 5px;
//     background-color: white;
//   }
// }
// .op-options {
//   padding: 0.5rem;
//   display: flex;
//   align-items: center;
//   justify-content: flex-end;
//   height: 2.5rem;
//   & i {
//     margin: 0 10px;
//     font-size: 0.86rem;
//   }
//   span {
//     i {
//       margin: 0;
//       font-size: 0.76rem;
//     }
//   }
// }
// .example-source-wrapper {
//   display: none;
//   .source {
//     background-color: #f5f7fa;
//     overflow-x: auto;
//     width: 100%;
//     pre {
//       position: relative;
//       z-index: 1;
//       margin: 0;
//       padding: 0.25rem;
//       background: transparent;
//       overflow-x: auto;
//       code {
//         text-align: left;
//         white-space: pre;
//         word-spacing: normal;
//         word-break: normal;
//         word-wrap: normal;
//         tab-size: 4;
//         hyphens: none;
//       }
//     }
//   }
// }
// .show {
//   display: block !important;
// }
// .source-control {
//   align-items: center;
//   justify-content: center;
//   border-top: 1px solid #dcdfe6;
//   height: 44px;
//   box-sizing: border-box;
//   background-color: #fff;
//   border-bottom-left-radius: 4px;
//   border-bottom-right-radius: 4px;
//   margin-top: -1px;
//   color: #909399;
//   cursor: pointer;
//   position: sticky;
//   left: 0;
//   right: 0;
//   bottom: -25%;
//   z-index: 10;
//   span {
//     margin-right: 4px;
//   }
// }
// .code_editor {
//   width: 100% !important;
//   // height: 600px !important;
//   & .code_area {
//     // height: 600px !important;
//     overflow: auto !important;
//   }
//   & .header {
//     padding: 20px 10px !important;
//   }
// }
// .source .code_editor > .code_area {
//   overflow: auto !important;
// }
// .key {
//   font-weight: 600;
//   font-size: 16px;
//   &.sec {
//     font-weight: 600;
//     font-size: 14px;
//     margin-left: 25px;
//   }
// }
// .secondary-key {
//   border-radius: 4px;
//   background: #d4d4d4;
//   &.opt {
//     color: #777ddb;
//   }
//   &.opt-val {
//     font-size: 12px;
//     color: #3f3f3f;
//   }
//   &.mand {
//     color: #be3333;
//   }
// }
// .sec-value {
//   margin-left: 25px;
// }
// .value {
//   font-size: 0.76rem;
// }
// pre {
//   background: #e0e0e075;
//   color: #000000;
// }
// p > code {
//   background: #80808042;
//   border-radius: 5px;
// }
</style>
