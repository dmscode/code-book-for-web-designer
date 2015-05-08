第四十七章 嗯哼，那只按钮会跳舞（一）
===

今天我有一个任务，要让一个按钮悦动起来。但是我们还有一些小限定，就是不能修改如下的 HTML 结构。换言之，在如下基础上我们只可以增加 css 和 js ，来达到我们的目的。

	<!DOCTYPE html>
	<html lang="en">
	<head>
		<meta charset="UTF-8">
		<title>跃动的按钮</title>
		<style>
			#button {
				width: 100px;
				height: 40px;
				margin:100px auto;
				padding: 30px 0;
				background: #EEE;
				line-height: 20px;
				text-align: center;
			}
		</style>
	</head>
	<body>
		<div id="button">
			点我<br>
			我会跳舞
		</div>
	</body>
	</html>

好啦，好简单的一个页面，我都有点不忍心去看呢……我们现在要添加东东了哦~~

引入 JQuery 然后加个 script标签准备写点高能的东西。

	<script src="http://upcdn.b0.upaiyun.com/libs/jquery/jquery-2.0.3.min.js"></script>
	<script type = "text/javascript">
		一会我们主要在这里写
	</script>

准备工作占了好多篇幅啊。要不我就让按钮跳两下咱就算搞定好不好？别扔鸡蛋……后边那个举着袜子的你是几个意思？我写个复杂的还不行么？

然后我刷刷点点写下了如下代码：

	$(document).ready(function(){
		$("#button").click(function(){
			$(this).animate({borderRadius:'50px'},1000);
			$(this).animate({borderRadius:'0px'},1000);
			$(this).animate({borderRadius:'50px'},1000);		
		});
	});

这里要着重说明一下：**animate 是排队进行的，一个做完才做下一个。**想一想跟前边的区别，所以我没用回调函数一层套一层的去写。

那么我们很容易理解上面的效果，方的变成圆的，再变成方的，再变成圆的，好像绕口令，我把速度写的慢了一点，这样大家可以清楚的看到效果。

当然了，就这么闪两下肯定不算完，我们还要让他缩小一下，但是缩小就比较麻烦了，因为我们要同时变化如下内容：宽度变小、上下内补变小。你说就这些？当然不是，上面的外补也得变，否则这个按钮的中心就动了位置了，那样看起来难受。你看我们上面刚说了，animate 是排队进行的，你让我一下子变这么多，还得同时，怎么搞？

其实写在一起就行了，就像这样：

	$(this).animate({width:'70px',paddingTop:"15px",paddingBottom:"15px",marginTop:"115px"},1000);

注意看标点啊！标点对了就差不多了。然后想想这些数值是为什么。

现在好像有点意思了，但是其实我们的游戏才刚刚开始。好了，下一节再见。