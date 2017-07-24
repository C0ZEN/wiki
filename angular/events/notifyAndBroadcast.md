// Subscribe to the notify on this factory for the user
function subscribe(scope, callback) {
    var handler = $rootScope.$on('usersFactoryUserChanged', callback);
    scope.$on('$destroy', handler);
}

// Notify the send message when subscribe is on
function _notify() {
    $rootScope.$emit('usersFactoryUserChanged');
}
