---
title: vue-more-preview图片预览插件(基于vue-preview插件的修改版)
date: 2018-03-08
categories: VUE
tags: VUE vue-more-preview vue-preview
---

[vue-more-preview](https://github.com/Likely6/vue-more-preview)是基于[vue-preview](https://www.npmjs.com/package/vue-preview)的图片预览插件，它修复了vue-preview引用时报错的bug，同时为options参数增加了style字段，以解决同页面里多区块中需要图片预览时出现的问题。

>这是图片预览的效果图。可以左右滑动切换图片，缩放图片等。

<img width="200" height="360" src="https://www.moment16.com/likely6/images/VUE_vue-moew-preview-01.jpg" style="margin: 0 auto"/>

>npm安装
{% highlight r%}
npm i vue-more-preview --save
{% endhighlight %}

>main.js引入
{% highlight r%}
import VueMorePreview from 'vue-more-preview'
Vue.use(VueMorePreview)
{% endhighlight %}

>例子 这个例子就展示了当要在两个区块内分别预览图片时的情况。

>vue-more-preview除了为options增加了一个style参数，其他使用都一样，具体使用参考[vue-preview](https://www.npmjs.com/package/vue-preview)
{% highlight r%}
<template>
  <div class="showA">
	<img class="preview-imgA" v-for="(item, index) in listA" :src="item.src" @click="openA(index)">
  </div>
  <div class="showB">
	<img class="preview-imgB" v-for="(item, index) in listB" :src="item.src" @click="openB(index)">
  </div>
</template>
<script>
export default {
	data () {
		return {
			#注意这里的listA里的字段名必须按以下示例的名称命名
			listA: [{
				src: 'https://placekitten.com/600/400',
				w: 600,
				h: 400
			}],
			listB: [{
				src: 'https://placekitten.com/600/400',
				w: 600,
				h: 400
			}, {
				src: 'https://placekitten.com/1200/900',
				w: 1200,
				h: 900
			}]
		}
	},
	methods: {
		openA(index) {
			$preview.open(index, this.listA, {
				style: '.preview-imgA'
			})
		},
		openB(index) {
			$preview.open(index, this.listB, {
				style: '.preview-imgB'
			})
		}
	}
}
</script>
{% endhighlight %}