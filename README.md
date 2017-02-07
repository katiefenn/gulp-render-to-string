# gulp-render-to-string
A Gulp plugin for injecting piped content into a [React](https://facebook.github.io/react/) element and rendering to it to a string using ReactDOM. This plugin is an alternative to templating content using [gulp-handlebars](https://www.npmjs.com/package/gulp-handlebars).

## Installation
This package is installed using [npm](https://www.npmjs.com/):

```
npm install gulp-render-to-string
```

## Options
### component
The React component to be rendered to a string. The content of files piped in will be passed to the component as the `children` prop.

### props
Props to pass to the component.

## Examples
```
// articles/article.html:
// <h1>Hello World</h1>

class Article {
  render() {
    return (
      <article className={ this.props.className }>
        { this.props.children }
      </article>
    );
  }
}

gulp.task('articles', function() {
  return gulp.src('articles/*')
    .pipe(renderToString(Article, { className: "article" }))
    .pipe(gulp.dest('./dist'));
});

// dist/articles/article.html:
// <article class="article" data-reactroot="" data-reactid="1" data-react-checksum="1365250946">
//   <h1>Hello World</h1>
// </article>
```
