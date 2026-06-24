bundle exec jekyll serve --livereload --trace --incremental

bundle exec jekyll serve --source . --destination docs

bundle exec jekyll build

magick mogrify -format webp -resize 1200x -strip -quality 70 *.jpg
