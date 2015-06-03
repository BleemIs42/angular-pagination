Angular-pagination

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
        <pagination currentPage="0" itemsPerPage="4"
        itemsList="musicEmotion" pageList="2"></pagination>

js:
angular.module('pagination.directives', []);

music.directive('pagination', function (){
    return {
        restrict: 'AE',
        replace: true,
        template: '\
            <div>\
                <span ng-click="jumpHead()">首页</span> \
                <span ng-click="prevPage()" ng-disabled="prevPageDisabled()">上一页</span>\
                <sapn ng-hide="prevPageDisabled() || (currentNum+1<=1)">...</sapn> \
                <span ng-repeat="num in number | \
                offset: currentNum*pageList | \
                        limitTo: pageList" \
                        ng-click="jumpPage(num)" \
                        ng-class="{numactive: currentPage+1 == num}">{{num}}</span> \
                <sapn ng-hide="nextPageDisabled() || (total<=pageList)">...</sapn> \
                <span ng-click="nextPage()" ng-disabled="nextPageDisabled()">下一页</span>\
                <span ng-click="jumpEnd()">尾页</span> \
            </div>',
        link:function (scope, element, attrs){

            scope.currentPage = attrs.currentpage;
            scope.itemsPerPage = attrs.itemsperpage;
            scope.itemsList = attrs.itemslist;
            scope.pageList = attrs.pagelist;

            scope.itemsList = scope.$eval(scope.itemsList);

            console.log(scope.itemsList);
            scope.pageCount = function () {
                if (scope.itemsList) {
                    return Math.ceil(scope.itemsList.length / scope.itemsPerPage);
                } else {
                    return 1;
                }
            };
            scope.total = scope.pageCount();

            scope.number = [];
            for(var i=0; i<scope.total; i++){
                scope.number.push(i+1);
            };

            scope.currentNum = 0;
            scope.jumpPageList = function (){
                scope.currentNum = parseInt(scope.currentPage/scope.pageList);
            };

            scope.jumpPage = function (num){
                scope.currentPage = num -1;
                scope.jumpPageList();
            };

            scope.jumpHead = function (){
                scope.currentPage = 0;
                scope.jumpPageList();
            }

            scope.jumpEnd = function (){
                scope.currentPage = scope.total-1;
                scope.jumpPageList();
            }

            scope.prevPage = function () {
                if(scope.prevPageDisabled()){
                    return;
                }
                if (scope.currentPage > 0) {
                    scope.currentPage--;
                }
                scope.jumpPageList();
            };

            scope.prevPageDisabled = function () {
                return scope.currentPage +1 == 1;
            };

            scope.nextPage = function () {
                if(scope.nextPageDisabled()){
                    return;
                }
                if (scope.currentPage < scope.pageCount()) {
                    scope.currentPage++;
                }
                scope.jumpPageList();
            };

            scope.nextPageDisabled = function () {
                return (scope.currentPage +1) == scope.total;
            };
        }
    }
});
```
