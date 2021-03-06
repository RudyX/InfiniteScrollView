# InfiniteScrollView
Swift 无限循环 ScrollView 自定义Page Control

##简单介绍
使用Swift语言和iOS SDK8 实现循环滚动效果；可用于首页banner，展示活动或者广告等信息。自定义UIScrollView, 内嵌UIImageView， 可从网络拉取数据进行填充，方便结合SDWebImage等第三方库进行扩展。本例仅仅是一个小Demo, 所用图片均在ImageSet中, 并未从网络拉取(原版OC实现了网络拉取).同时实现了自定义page control, 不同于自带圆点page control, 本例使用bottom bar做page control, 可自定义颜色；By the way, 定义了UIColorFromRGB函数, 方便直接取16进制颜色代码拷贝。仔细阅读源代码,十分方便扩展，今后也可能会持续更新，完善。

HYInfiniteScrollView的逻辑较为复杂, 不类似UITableView的内存重用的管理方式(本人还有另一个控件--照片浏览控件，实现了UITableView式的重用机制，稍后分享)。 基本考虑了所有边界情况(1张，2张和多张情况), 原版上线未出bug。

##如何使用
本控件使用时只需要初始化和设定几个参数值即可, 关键代码如下: 

   
	                         
	let scrollViewRect: CGRect = CGRectMake(0, self.navigationController!.navigationBar.bounds.height, self.view.bounds.width, 200)
	
    self.scrollView = HYInfiniteScrollView.init(frame: scrollViewRect)
    self.scrollView.autoresizingMask = UIViewAutoresizing.FlexibleWidth |   
                                       UIViewAutoresizing.FlexibleHeight
    self.scrollView.animationEnable = true
    self.scrollView.animationDuration = 3.0
    self.scrollView.slideBarEnable = true
    self.scrollView.delegate = self
	
	let imgArr: NSArray = [1,2,3,4,5]
    self.scrollView.reloadActivityItem(imgArr)
        
    self.view.addSubview(self.scrollView)
	
	
    
    
    
reloadActivityItem 这个方法是外界传参的接口, 本Demo传入值很简单，只起到循环作用，原版OC封装了自己的数据类和相应接口，诸位可以自己扩展。

另外有些delegate没有实现，但不影响功能。


##截图如下：

![Mou icon](http://zhgyw.cn/images/1-test.jpg) 
![Mou icon](http://zhgyw.cn/images/2-test.jpg)