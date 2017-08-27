# Directive template with his own controller

### Why ?

I just wanted to share the very basic creation of a directive which will be used as element.  
This kind of directive is often complex and with the time, grow bigger and bigger.

The base should be very solid, so, take a look at the syntax, I think it's a good one.

### Directive

```
/**
 * @ngdoc directive
 * @name capricieuseApp.directive:cozen-btn
 * @scope
 * @restrict E
 * @replace false
 * @transclude false
 *
 * @description
 *
 * [Scope params, one-way binding]
 * @param {string} cozenBtnLabel > Label [translate]
 *
 * [Scope params, two-way binding]
 *
 * [Attrs params]
 * @param {function} cozenBtnOnClick > Callback function called on click
 *
 */
(function (angular) {
    'use strict';

    angular
        .module('capricieuseApp')
        .directive('cozenBtn', cozenBtn);

    cozenBtn.$inject = [];

    function cozenBtn() {
        return {
            link            : link,
            restrict        : 'E',
            replace         : false,
            transclude      : false,
            scope           : {
                cozenBtnLabel: '@'
            },
            templateUrl     : 'scripts/directives/ui/btn/btn.template.html',
            controller      : 'cozenBtnController',
            controllerAs    : 'vm',
            bindToController: true
        };

        function link(scope, element, attrs) {
            var methods = {
                init   : init,
                destroy: destroy
            };

            methods.init();

            // Execute the one shot stuff on creation of the directive
            function init() {

                // Destroy listeners
                element.on('$destroy', methods.destroy);
                scope.vm.data.listeners.push(scope.$on('$destroy', methods.destroy));
            }

            // Unbind and destroy all listeners and watchers
            function destroy() {
                element.off('$destroy', methods.destroy);
                angular.forEach(scope.vm.data.listeners, function ($listener) {
                    $listener();
                });
            }
        }
    }

})(window.angular);
```

### Controller

```
/**
 * Created by C0ZEN on 27/08/2017.
 */
(function (angular) {
    'use strict';

    angular
        .module('capricieuseApp')
        .controller('cozenBtnController', cozenBtnController);

    cozenBtnController.$inject = [
        'logsService',
        '$scope',
        '$attrs',
        'config'
    ];

    function cozenBtnController(logsService, $scope, $attrs, config) {
        var vm = this;

        // Common data
        vm.data = {
            controller: 'cozenBtnController',
            directive : 'cozenBtn',
            listeners : [],
            debug     : config.directives.btn.debug
        };

        // Public methods
        vm.methods = {
            onClick: onClick
        };

        function onClick($event) {
            if (vm.data.debug) {
                logsService.info.functionCalled(vm.data.controller, 'onClick');
            }
            $event.stopPropagation();
            $scope.$eval($attrs.cozenBtnOnClick);
        }
    }

})(window.angular, document);
```
