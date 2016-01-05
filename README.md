# TankCarouselFigure
轮播图

添加方法
 TankCycleScrollView *cycleView = [[TankCycleScrollView alloc] initWithFrame:CGRectMake(0, 0, [UIScreen mainScreen].bounds.size.width, 200) animationDuration:2];

// 传递图片数组时既能传递本地图片 使用（cycleImageArray）  如果是网络图片使用（cycleImageUrlArray）

//    cycleView.cycleScrollPageControlAliment = TankCyclePageContolAlimentCenter; //设置PageControl的位置 
//    self.cycleView = cycleView; //用于设置拉伸效果时
//    cycleView.enbleStretch = YES; //设置是否有拉伸效果
//    cycleView.TapActionBlock = ^(NSInteger pageIndex, id model){
        NSLog(@"%d ,%@",pageIndex,[(TankCycleImageModel *)model attractionId]);
    }; //点击时参数传递及跳转
    
1、直接添加  直接添加到需要添加的View上

2、
在使用时可以放到UITableView的TableHeaderView 上可以设置拉伸效果   
设置拉伸效果时需设置cycleView.enbleStretch = YES;
并且实现tableview实现UIScrollViewDelegate的- (void)scrollViewDidScroll:(UIScrollView *)scrollView

// UIScrollViewDelegate
- (void)scrollViewDidScroll:(UIScrollView *)scrollView
{
    CGFloat offsetY = scrollView.contentOffset.y;
    if (offsetY < 0) {
        // 添加上这个限制出现类似微博那种拉伸一半 可以自己设置拉伸位置
//        if (offsetY > -100) {
            [self.cycleView cycleScrollViewStretchingWithOffset:offsetY];
//        }
    }
}
