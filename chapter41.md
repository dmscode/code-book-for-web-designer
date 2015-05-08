第四十一章 加点 JavaScript
===

就是我们平时说的 JS 啊。我们说 HTML 是骨头，CSS 是肉，那 JS 是啥？是生命啊。因为 JS 可以让你的网页动起来，这是一件十分美妙的事情啊！

然后哈，JavaScript 跟 Java 没啥关系，以后别再拿它俩攀亲戚了，这误会可有点大。好了，不废话了，我们来讲讲怎么在网页里插入 JS 。

三种办法，跟 css 的感觉差不多，所以也挺好理解的。第一种，直接写在代码里，其实我也很少用，而且我也不建议用，想找着维护挺麻烦的。比如说下面的代码：

	<div id="box" onclick="alert('我就是问候一下，没别的事');"></div>

第二种就是直接写在 head 里面，比如：

	<!DOCTYPE html>
	<html lang="en">
	<head>
		<meta charset="UTF-8">
		<title>我不喜欢 JS</title>
		<script type = "text/javascript">
			alert("我又来了，不管你烦不烦我");
		</script>
	</head>
	<body>
		……
	</body>
	</html>

第三种就是把 js 写在一个单独的文件里，然后在网页文件里调用，像这样：

	<!DOCTYPE html>
	<html lang="en">
	<head>
		<meta charset="UTF-8">
		<title>我不喜欢 JS</title>
		<script src="js/script.js"></script>
	</head>
	<body>
		……
	</body>
	</html>

你要是理解了 css 的插入方法，这里其实很简单了，悄悄告诉你，下节课我们说点好玩的