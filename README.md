# node-connect-datadog

Datadog middleware for Connect.js / Express.js


## Usage

```
npm install git://github.com/cladeco/node-connect-datadog.git#master -S
```

Add middleware immediately before your router.

```js
const connectDatadog = require("connect-datadog")
app.use(connectDatadog({}))
app.use(app.router)
```

## StatsD Client Arguments

You can also pass arguments to the StatsD Client after your options:

```js
connectDatadog()
app.use(connectDatadog({
  tags: ['some:tag']
}, 'some.hostname', 8125))
```

## Options

All options are optional.

* `dogstatsd` node-dogstatsd client. `default = new (require("node-dogstatsd")).StatsD()`
* `stat` *string* name for the stat. `default = "buffer.server"`
* `tags` *array* of tags to be added to the histogram. `default = []`
* `sampleRate` *number* sends only a sample of data to StatsD `default: 1`
* `path` *boolean* include path tag. `default = false`
* `method` *boolean* include http method tag. `default = false`
* `protocol` *boolean* include protocol tag. `default = false`
* `response_code` *boolean* include http response codes. `default = false`
* `statsCallback` *function* callback hook that provides the following params

```js
(datadog, stat, sampleRate, statTags, req, res) => {
  // increment coolthing
  datadog.increment(`${stat}.coolthing`, sampleRate, statTags);
}
```

## License

View the [LICENSE](https://github.com/AppPress/node-connect-datadog/blob/master/LICENSE) file.
