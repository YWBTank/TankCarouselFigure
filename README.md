# TankCarouselFigure
轮播图


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
