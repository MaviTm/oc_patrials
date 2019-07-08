const gulp = require('gulp');
const browserSync = require('browser-sync').create();
const sass = require('gulp-sass');
const minifyCSS = require('gulp-csso');
const minifyImg = require('gulp-imagemin');
const minifyJS = require('gulp-uglify');
const minifyHTML = require('gulp-htmlmin');
const concat = require('gulp-concat');
const autoprefixer = require('gulp-autoprefixer');
const del = require('del');
const runSequence = require('run-sequence');

gulp.task('css', ()=>{
    return gulp.src('scss/**/*.scss')
        .pipe(sass({
            outputStyle: 'nested',
            precision: 10,
            includePaths: ['.']
        }).on('error', sass.logError))
        .pipe(minifyCSS())
        .pipe(autoprefixer())
        .pipe(concat('app.min.css'))
        .pipe(gulp.dest('css'));
});

gulp.task('js', () => {
    return gulp.src('sourcejs/**/*.js')
        .pipe(concat('app.min.js'))
        .pipe(minifyJS())
        .pipe(gulp.dest('js'));
});

gulp.task('watch', () => {
    gulp.watch("scss/**/*.scss", ['css']);
    gulp.watch("sourcejs/**/*.js", ['js']);
});

gulp.task('default', () => {
    runSequence(
        'css',
        'js',
        'watch'
    );
});
