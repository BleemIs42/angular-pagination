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

    //
    //currentPage: The number of pages minus one
    //itemsPerPage: items for ng-repeat
    //itemsList: the object or array for ng-repeat
    //pageList: the num of pagination length
    //numactive: class for current page color
    <pagination currentPage="0" itemsPerPage="4"
    itemsList="musicEmotion" pageList="2"></pagination>

js:
    app.controller('AppCtrl', ['$scope', function ($scope){
    //use api data replace $scope.musicEmotion
    $scope.musicEmotion = [
        {
            'num': '一',
            'name': '红尘客栈'
        },

        {
            'num': '二',
            'name': '红尘客栈'
        },

        {
            'num': '三',
            'name': '红尘客栈'
        },

        {
            'num': '四',
            'name': '红尘客栈'
        },

        {
            'num': '五',
            'name': '红尘客栈'
        },

        {
            'num': '六',
            'name': '红尘客栈'
        },

        {
            'num': '七',
            'name': '红尘客栈'
        },

        {
            'num': '八',
            'name': '红尘客栈'
        },

        {
            'num': '九',
            'name': '红尘客栈'
        },

        {
            'num': '十',
            'name': '红尘客栈'
        },

        {
            'num': '十一',
            'name': '红尘客栈'
        },

        {
            'num': '十二',
            'name': '红尘客栈'
        },

        {
            'num': '十三',
            'name': '红尘客栈'
        },

        {
            'num': '十四',
            'name': '红尘客栈'
        }
    ];
    $scope.$broadcast('musicEmotion');
}]);
```