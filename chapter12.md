第十二章 css 的书写格式
===

按着我的个人习惯 css 与 html 分离，两个文件在编辑器里左一个右一个，同步编写。html 写下结构，css 里就写对应的样式。那么比如我写下了如下的 html

	<!doctype html>
	<html lang="en">
		<head>
			<meta charset="UTF-8">
			<title>Document</title>
			<link rel="stylesheet" type="text/css" href="style.css" />
		</head>
		<body>
			<div id="topbox">Lorem ipsum dolor sit amet, consectetur adipisicing elit. Voluptatibus, delectus, quas, sapiente, hic vero quos eveniet doloremque iste neque molestias explicabo aperiam possimus consequuntur eligendi a rerum suscipit perferendis quae?</div>
			<div class="box">Lorem ipsum dolor sit amet, consectetur adipisicing elit. Adipisci, totam neque non quam reiciendis itaque distinctio nesciunt! Repudiandae, architecto sint quod pariatur magnam ex neque dolorum repellendus quisquam culpa minus.</div>
			<div class="box">Eum, placeat, illum, nobis at doloremque ut perspiciatis dolor vel perferendis debitis commodi voluptatibus a hic? Assumenda, soluta, voluptate maiores laborum id nobis fugiat in praesentium repellat maxime velit necessitatibus.</div>
		</body>
	</html>

然后我就要在这个 html 文件所在目录新建一个 文件，名叫 style.css （被引用的 css 文件名）。然后在这个 css 文件里些如下内容

	/* 这里是CSS 的注释，你爱写点啥写点啥 */
	#topbox {
		color:red;
	}
	.box {
		color:blue;
	}

其实就是

> 选择器 {属性:属性值;}

然后属性和属性值可以多次重复，就像下面：

	#topbox {
		color:red;
		width:100px;
		height:300px;
	}

其实你都写在一行也行，我一个属性一行，前边还有缩进纯粹是为了便于阅读。所以还有 css 压缩一说，就是把 css 文件里所有不必须的空白和换行全部去掉，这样可以减小 css 文件的体积。当然这样的文件想要阅读……代码高亮了也如线团一般，所以我都是冲洗格式化以后再读。

然后在 html 中的属性值很多都不带单位，比如 width=100 就是宽度是 100 像素。但是在 CSS 里则必须带上单位 width:100px; 才行。