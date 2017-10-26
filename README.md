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

**发现压缩后代码丢失，暂时还没找到解决办法**





## 参考文章
