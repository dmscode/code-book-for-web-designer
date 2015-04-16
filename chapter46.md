第四十六章 继续玩（三）
===

鉴于即将产生的混乱情况，所以我们要来使用函数了，正经的用一用这个塑料袋哦。

	function 函数名(参数){函数的主要代码}

这是比较正经的格式，参数可有可无，我们以前当塑料袋用的时候连函数名都省了。这个问题是酱紫的，你手里有个塑料袋，那我说你手里那个塑料袋就很明确了。但是要是那边一堆塑料袋，我就得说，去，把那个写着老王家小卖部的塑料袋拿过来，你才明白是哪一个。

好，现在我们写两个函数 a 和 b ，a 负责变长， b 负责变短。因为就两个函数，我就不取复杂的名字了。

	function a(){
		b();
	}
	function b(){
		a();
	}

现在假如我运行了 a() 也就是调用函数 a，然后呢执行 a 里面的代码，运行函数 b，然后运行 b 里面的代码，执行函数 a ……如此往复，无休无止，好像就是我们需要的效果了。那就开始改造。

	function a(){
		$("#cz").animate({width:'20px'},1000,function(){
			windowswidth=$(window).width();
			x=$("#cz").offset();
			right=windowswidth-$("#cz").width()-x.left;
			$("#cz").css("left","auto");
			$("#cz").css("right",right+"px");
			b();
		});
	}

这部分基本不再需要解释了吧，就是把上一节的代码放进了函数 a 里，然后加上了对函数 b 的调用。然后写 函数 b

	function b(){
		$("#cz").animate({width:'15px'},1000,function(){
			x=$("#cz").offset();
			$("#cz").css("right","auto");
			$("#cz").css("left",x.left+"px");
			a();
		});
	}

这个就没啥可说了，你认真看看就懂。最后，虽然我们定义了两个函数，但是注意只是定义啊，定义和运行是两码事。我们要给他一个开始，所以要在 $(document).ready 里调用一下函数 a。好了，下面是完整的代码，其中有些数值我稍微修改了一下，以使效果更舒服。

	<!DOCTYPE html>
	<html lang="en">
		<head>
			<meta charset="UTF-8">
			<title>我是一只小虫子，不呀不着急</title>
			<style>
				#cz {
					position: absolute;
					left: 10px;
					top: 50px;
					height: 5px;
					width: 15px;
					background:#393;
				}
			</style>
			<script src="http://upcdn.b0.upaiyun.com/libs/jquery/jquery-2.0.3.min.js"></script>
			<script type = "text/javascript">
				function a(){
					$("#cz").animate({width:'30px'},600,function(){
						windowswidth=$(window).width();
						x=$("#cz").offset();
						right=windowswidth-$("#cz").width()-x.left;
						$("#cz").css("left","auto");
						$("#cz").css("right",right+"px");
						b();
					});
				}
				function b(){
					$("#cz").animate({width:'15px'},600,function(){
						x=$("#cz").offset();
						$("#cz").css("right","auto");
						$("#cz").css("left",x.left+"px");
						a();
					});
				}
				$(document).ready(function(){
					a();
				});
			</script>
		</head>
		<body>
			<div id="cz"></div>
		</body>
	</html>

对了，这只傻虫子，只会爬，不会停……