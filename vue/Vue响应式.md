## Vue响应式

### 简单式

``` html
<!doctype html>
<html>
    <head>
        <title>test vue</title>
    </head>
    <body id="demo"></body>
    <script>
        class Vue {
            constructor(options) {
                this.$options = options
                this._data = options.data
				Object.keys(options.data).forEach(key => this._proxy(key, this._update))
                this._update()
            }
            _update() {
                this.$options.render()
            }
			_proxy(key, cb) {
				const self = this
				Object.defineProperty(self, key, {
				  configurable: true,
				  enumerable: true,
				  get: function proxyGetter () {
					return self._data[key]
				  },
				  set: function proxySetter (val) {
					self._data[key] = val;
					cb.call(self);
				  }
				})
			}
        }

        var demo = new Vue({
            el: 'demo',
            data: {
                text: 123,
            },
            render() {
				document.getElementById(this.el).innerHTML = this.data.text
            }
        })

        setTimeout(function() {
            demo.text = 444
        }, 3000)
    </script>
</html>
```
