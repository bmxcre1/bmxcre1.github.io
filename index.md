(function workerFn() {
    var _this = this;

    var interval = void 0;
    this.onmessage = function (e) {
        switch (e.data) {
            case true:
                if (!interval) {
                    interval = setInterval(function () {
                        _this.postMessage(true);
                    }, 1000 / 30);
                }
                break;
            case false:
                if (interval) {
                    clearInterval(interval);
                    interval = 0;
                }
                break;
            default:
                _this.postMessage(e.data);
                break;
        }
    };
})()
