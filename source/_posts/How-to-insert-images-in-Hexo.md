---
title: How to insert images in Hexo?
date: 2017-06-25 10:55:35
tags: Hexo tutorial
---

A very good [tutorial](https://yanyinhong.github.io/2017/05/02/How-to-insert-image-in-hexo-post/) about using local images, as briefly summarized below

1. Change in ```_config.yml```: ```post_asset_folder: true```
2. ```npm install https://github.com/CodeFalling/hexo-asset-image --save``` ([ref](http://www.jianshu.com/p/c2ba9533088a))
3. Use ```Hexo new "name of new file"``` to create a new ```.md``` file and accordingly, a folder with the same name ```name-of-new-file``` is created to store the image files. For example, image file ```Absorption Cross Section.png```.
4. Cite the image file with ```![](name-of-new-file/Absorption Cross Section.png)```.