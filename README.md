#[Angular-pagination](http://shafley.github.io/learn/pagination/)

[Demo:shafley.github.io/learn/pagination/](http://shafley.github.io/learn/pagination/)

### Install
    npm install angular-pagination
### How to use
```javascript
html:
    <li class="talk-music-pic"
        ng-repeat="music in musicEmotion |
        offset: currentPage*itemsPerPage |
        limitTo: itemsPerPage">Pagination</li>;

    //currentPage: number      当前页码-1
    //itemsPerPage: number     ng-repeat每页显示的list长度
    //itemsList: array         ng-repeat渲染的数组
    //pageList: number         分页显示的页码数字个数
    //numactive: class         当前页页码的样式(背景颜色)
    <pagination currentPage="0" itemsPerPage="4"
    itemsList="musicEmotion" pageList="2"></pagination>
```
```javascript
js:
    app.controller('AppCtrl', ['$scope', function ($scope){
    //后台返回的数据替换 $scope.musicEmotion
    $scope.musicEmotion = [{}, {}, {}, {}, {}, {}];
    $scope.$broadcast('musicEmotion');
}]);
```
