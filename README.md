# gulp常用插件及使用方法

测一下gulp常用插件的使用方法

## CSS压缩 

[使用 gulp-csso](https://github.com/ben-eb/gulp-csso)

npm

```
npm install gulp-csso --save-dev
```
example

```
var gulp = require('gulp');
var csso = require('gulp-csso');

gulp.task('csso', function () {
  return gulp.src('src/index.css')
    .pipe(csso({
      restructure: false,
      sourceMap: true,
      debug: true
    }))
    .pipe(gulp.dest('output/minCss'));
});
```

csso 参数配置详情参见： [https://github.com/ben-eb/gulp-csso#api](https://github.com/ben-eb/gulp-csso#api)

## JS压缩

[使用 gulp-uglify](https://github.com/terinjokes/gulp-uglify)

**该插件会优化js代码去除掉未引用的变量和方法**

npm

```
npm install --save-dev gulp-uglify
```

example

```
var gulp = require('gulp');
var uglify = require('gulp-uglify');
var pump = require('pump');

gulp.task('compress', function (cb) {
  pump([
        gulp.src('lib/*.js'),
        uglify(),
        gulp.dest('dist')
    ],
    cb
  );
});
```

## html压缩

[使用 gulp-minify-html](https://github.com/sanfords/gulp-minify-html)

npm

```
npm install gulp-minify-html --save-dev
```

example

```
var gulp = require('gulp');
var minifyHTML = require('gulp-minify-html');

gulp.task('minify-html', function() {
  var opts = {comments:true,spare:true};
  gulp.src('src/*.html')
  .pipe(minifyHTML(opts))
  .pipe(gulp.dest('output/minHTML'))
});
```

**不会去压缩html文件内的css和js代码**

## 图片压缩

[使用 gulp-imagemin](https://github.com/sindresorhus/gulp-imagemin)

npm

```
npm install --save-dev gulp-imagemin
```

example

```
const gulp = reuqire('gulp');
const imagemin = require('gulp-imagemin');

gulp.task('default', () =>
  gulp.src('src/img/*')
  .pipe(imagemin())
  .pipe(gulp.dest('output/imgMin'))
)
```

第一次安装的时候压缩报错，写在重装后就可以了。目前还不知道是什么原因。

还有一个问题，就是不知道怎么把被压缩的图片的具体信息log出来！！

更多图片压缩的api配置请参考：
> [https://github.com/sindresorhus/gulp-imagemin#api](https://github.com/sindresorhus/gulp-imagemin#api)
> 
> [http://www.ydcss.com/archives/26](http://www.ydcss.com/archives/26)

## js代码检查

[使用 gulp-jshint](https://github.com/spalger/gulp-jshint)

npm

```
npm install jshint gulp-jshint --save-dev
```

example

```
const gulp   = require('gulp');
const jshint = require('gulp-jshint');

gulp.task('lint', function() {
  return gulp.src('src/index.js')
    .pipe(jshint())
    .pipe(jshint.reporter());
});
```

使用时报错：`Error: Cannot find module 'jshint/src/cli`

原因： 没有仔细阅读readme说明，未安装`jshint`导致的

更多配置请参考：[https://github.com/spalger/gulp-jshint#options](https://github.com/spalger/gulp-jshint#options)

## 文件合并

[使用 gulp-concat](https://github.com/contra/gulp-concat)

npm

```
npm install gulp-concat --save-dev
```

example

```
var gulp   = require('gulp');
var concat = require('gulp-concat');

gulp.task('scripts', function(){
  return gulp.src('src/*.js')
  .pipe(concat('all.js'))
  .pipe(gulp.dest('output/total'));
});
```

更多配置参数请参考：

> [https://github.com/contra/gulp-concat#usage](https://github.com/contra/gulp-concat#usage)

暂时写这么多，后面用到什么在来补充。




## 参考文章

https://zhuanlan.zhihu.com/p/25243171