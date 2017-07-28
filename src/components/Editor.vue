<template>
  <div id='editor'>
    <nav>
      <ol>
        <li class="active">
          <svg class="icon"> 
            <use xlink:href="#icon-id"></use>
          </svg>
        </li>
        <li>
          <svg class="icon"> 
            <use xlink:href="#icon-work"></use>
          </svg>
        </li>
        <li>
          <svg class="icon"> 
            <use xlink:href="#icon-book"></use>
          </svg>
        </li>
        <li>
          <svg class="icon"> 
            <use xlink:href="#icon-project"></use>
          </svg>
        </li>
        <li>
          <svg class="icon"> 
            <use xlink:href="#icon-jiangbei"></use>
          </svg>
        </li>
        <li>
          <svg class="icon"> 
            <use xlink:href="#icon-lianxi"></use>
          </svg>
        </li>
      </ol>
    </nav>
    <ol class="panes"></ol>
  </div>
</template>


<style lang="scss">
  #editor {
    min-height: 100px;
    display: flex;

    > nav {
      width: 80px;
      background: #000;

      > ol > li {
        border: 1px solid blue;
        padding: 8px 0;
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
  }
</style>
