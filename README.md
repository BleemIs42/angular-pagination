#[Angular-pagination](http://shafley.github.io/learn/pagination/)

[Demo:shafley.github.io/learn/pagination/](http://shafley.github.io/learn/pagination/)

###Install
    npm install angular-pagination
```javascript
html:
    <li class="talk-music-pic"
        ng-repeat="music in musicEmotion |
        offset: currentPage*itemsPerPage |
        limitTo: itemsPerPage"> 分页分页分页</li>;

    //指令接口
    //currentPage: 当前页数-1
    //itemsPerPage: ng-repeat 显示的列表数目
    //itemsList: ng-repeat的数组(对象)
    //pageList: 显示的页码数目
    //numactive: 当前页码数字的颜色类样式(class)
    <pagination currentPage="0" itemsPerPage="4"
    itemsList="musicEmotion" pageList="2"></pagination>
```