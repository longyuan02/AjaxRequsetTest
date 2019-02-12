# vuefirstobject

> A Vue.js project

## Build Setup

``` bash
# install dependencies
npm install

# serve with hot reload at localhost:8080
npm run dev

# build for production with minification
npm run build

# build for production and view the bundle analyzer report
npm run build --report

# run unit tests
npm run unit

# run e2e tests
npm run e2e

# run all tests
npm test
```

For a detailed explanation on how things work, check out the [guide](http://vuejs-templates.github.io/webpack/) and [docs for vue-loader](http://vuejs.github.io/vue-loader).

### axios 基本使用方法  也可以使用 vue-resource
    axios.post(url,data,[options]);
    发送请求是格式为 Request Payload,并非常用的Forme Data格式
    所以参数必须要以键值对形式传递，不能以json格式传参
    传参方式：
    1.自己拼接为键值对
    2 .使用transformRequest,在请求发送前将数据进行转换
    3.使用第三方库。如果使用模块开发可以使用 qs querystring 进行转换
    axios 不支持跨域请求，只能使用第三方库

### 使用vue-resource 发送跨域请求
jsonp:cb 更改回调名称
使用this.$http发送请求
get(url, [options])
head(url, [options])
delete(url, [options])
jsonp(url, [options])
post(url, [body], [options])
put(url, [body], [options])
patch(url, [body], [options])


# AjaxRequsetTest
