# How to combine multiple text files in bash by number

In this scenario we have a bunch of files blah0.txt blah1.txt blah2.txt ...blah 10.txt ...blah 322.txt ... and want to combine them by number in a sorted fashion. I used this because I had 705 files, each one corresponded to a single simulation step and contained a single like of data. I wanted to combine them all together so that I could plot them

```
ls blah*.txt |sort --version-sort | xargs cat > blah_all.txt
```
