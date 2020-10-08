require 'asciidoctor'
require 'rake/clean'

OUTDIR = "public"
SOURCE_DOC = "src/index.adoc"
SOURCE_IMAGEDIR = "src/images"
ATTRIBUTES= "-a outdir=tmp -a imagesoutdir=#{SOURCE_IMAGEDIR} -a mmdc=node_modules/.bin/mmdc"
PDF_ATTRIBUTES= "-a pdf-theme=default-with-fallback-font -a outdir=tmp -a imagesoutdir=#{SOURCE_IMAGEDIR} -a mmdc=node_modules/.bin/mmdc"
PDF_FILE_NAME="book.pdf"
CLEAN.include(OUTDIR)

desc 'Generate the docs to HTML'
task :html do
  # public/index.htmlを生成
  sh "asciidoctor -r asciidoctor-diagram #{ATTRIBUTES} #{SOURCE_DOC} -o #{OUTDIR}/index.html"
  sh "cp -rp #{SOURCE_IMAGEDIR} #{OUTDIR}/images"
end

desc 'Generate the docs to PDF'
task :pdf do
  sh "asciidoctor-pdf -r asciidoctor-diagram #{PDF_ATTRIBUTES} #{SOURCE_DOC} -o #{OUTDIR}/#{PDF_FILE_NAME}"
end

task :default => [:html]