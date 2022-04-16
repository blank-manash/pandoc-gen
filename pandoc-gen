#!/usr/bin/bash
DATE="$(date +'%A, %d %B %Y')"

addMetaData() {
echo $1 >> meta.yaml
}

addDefault() {
arr=("geometry:" "\t- top=30mm" "\t- left=20mm" "\t- heightrounded" "output: pdf_document" "colorlinks: true")

for i in "${arr[@]}"; do
        echo -e "$i" >> meta.yaml
    done
}

read -p "Enter Title: " TITLE
read -p "Author: " AUTHOR
read -p "Table of Content: " TOC

echo "---" > meta.yaml
echo "title: $TITLE" >> meta.yaml
echo "author: $AUTHOR" >> meta.yaml
echo "date: $DATE" >> meta.yaml

if [[ $TOC == [yY] ]]; then
    echo "toc: true" >> meta.yaml
fi

addDefault

echo "---" >> meta.yaml

FILE="${1%.*}"
pandoc "$FILE.md" meta.yaml -o "$FILE.pdf"
rm meta.yaml
