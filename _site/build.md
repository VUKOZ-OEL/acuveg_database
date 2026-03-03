bundle exec jekyll serve --livereload --trace --incremental

bundle exec jekyll serve --source . --destination docs

destination: docs

magick mogrify -format webp -resize 1200x -strip -quality 70 *.jpg