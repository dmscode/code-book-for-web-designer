第四十三章 开始玩 JQ
===

嗯，努力点，免得反被 JQ 玩。这一次我没来做一个简单的，讨人厌的网页。用到 JQ 和一点简单的 JS。做出来是非常的讨人厌呢~

首先我们准备一个网页，这网页也很简单，就一个按钮，这个你们会写啊，来看看我写的。

	<!DOCTYPE html>
	<html lang="zh">
		<head>
			<meta charset="UTF-8">
			<title>我就是想气死你！</title>
			<style>
				button {
					width:160px;
					height: 38px;
					display:block;
					text-align: center;
					font-size: 18px;
					line-height: 38px;
					background: #F3F3F3;
					border:1px solid #DDD;
					margin:150px auto 0;
					box-shadow: 0 3px 12px #DDD;
					cursor: pointer;
				}
			</style>
		</head>
		<body>
			<button>有种你点我呀！</button>
		</body>
	</html>

我加了一些 css 样式，来让这个按钮看起来更讨厌一些……，现在我们开始赋予它灵魂！在 </style\> 标签后面填上

	<script src="http://upcdn.b0.upaiyun.com/libs/jquery/jquery-2.0.3.min.js"></script>
	<script type = "text/javascript">
		$(document).ready(function(){
			一会在这里写
		});
	</script>

这是一个很基础的结构，我们照抄过来，然后开始写（上面代码里标注了要在哪里写）

	$("button").mouseover(function(){
		$(this).css("margin-top","50px");
	});

来解释一下哦~ button 元素发生什么情况的时候呢？鼠标划到他的上面（mouseover），就执行后面括号里的代码。

那么括号里的代码会做些什么呢？首先说 this 指的是外层提到的元素，就是 button，它发生什么动作？他的 css 发生变化，就是后面括号里的 margin-top 变为 50px，比他以前的值（150px） 小了。

于是这个网页现在的效果就是，当你的鼠标移动到按钮上，按钮就往上移动了，于是你点不到他，但是你如果再次移动上去它就不动了，因为他现在的 margin-top 就是 50px，所以就没有变化了。

恶心人有了第一步是不够的，我们要切断他的一切希望，别以为你再追上去就可以点击了，哼哼，没那么容易的。

那么现在我们的想法是：鼠标划上去，按钮向上移动（已实现），再移上去，按钮向下移动，如此周而复始。

那么我们来说点相关知识：JQ 里有些事件不单单可以赋值，还能取值，比如：

	mt=$("button").css("margin-top");

mt 里就储存了 button 元素的 margin-top 属性值。

然后再将一个很有用的 JS 语句

	if (条件){
		条件成立时要执行的代码;
	}else{
		条件
	}

知道这两点我们就可以试试看了

	$("button").mouseover(function(){
		mt=$(this).css("margin-top");
		if (mt=="150px"){
			$(this).css("margin-top","50px");
		}else{
			$(this).css("margin-top","150px");
		}
	});

来看代码啊，首先当鼠标移动到 button 元素上的时候我们开始进行如下动作：

先是获取 button 的 margin-top 属性得值，存在 mt 里面。然后我们开始判断：如果 mt 等于（连续两个等号表示等于）150px ，就把 button 的 margin-top 属性设置为 50px，否则（就是 mt 不等于 150px 的时候），就把 button 的 margin-top 属性设置为 150px.

看着有点绕？就是如果是 150，就改成 50，如果不是 150，就改成 150。这样说就明白了。

试试吧，反正你点不着这个按钮。赶紧发到网上调戏好友去，但是别调戏女友，会被拍死的。

完整代码如下：

	<!DOCTYPE html>
	<html lang="zh">
		<head>
			<meta charset="UTF-8">
			<title>我就是想气死你！</title>
			<style>
				button {
					width:160px;
					height: 38px;
					display:block;
					text-align: center;
					font-size: 18px;
					line-height: 38px;
					background: #F3F3F3;
					border:1px solid #DDD;
					margin:150px auto 0;
					box-shadow: 0 3px 12px #DDD;
				}
			</style>
			<script src="http://upcdn.b0.upaiyun.com/libs/jquery/jquery-2.0.3.min.js"></script>
			<script type = "text/javascript">
				$(document).ready(function(){
					$("button").mouseover(function(){
						mt=$(this).css("margin-top");
						if (mt=="150px"){
							$(this).css("margin-top","50px");
						}else{
							$(this).css("margin-top","150px");
						}
					});
				});
			</script>
		</head>
		<body>
			<button>有种你点我呀！</button>
		</body>
	</html>