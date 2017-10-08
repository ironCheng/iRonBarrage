#  iRonBarrage
a Barrage Kit for iOS / iOS 弹幕控件

<p>
  
## 使用方法-Usage

参考viewController<br>
<pre><code>
1、#import "iRonBarrage.h"，并遵守协议 /<iRonBarrageDataSource/> <br>
2、 _manager = [iRonBarrage shareInstance];
    _manager.showingView = self.view;
    _manager.scrollSpeed = 90;
    _manager.refreshInterval = 0.5;
    _manager.displayLocation = iRonBarrageDisplayLocationTypeTop;
    
    _manager.dataSource = self;
    [_manager startScroll];
3、dataSource里
  - (id)dataSourceForTheBarrage:(iRonBarrage *)barrage
{
    int a = arc4random() % 10000;
    NSString *str = [NSString stringWithFormat:@"%d",a];
    NSMutableAttributedString *attr = [[NSMutableAttributedString alloc] initWithString:str];
    [attr addAttribute:NSForegroundColorAttributeName value:RandomColor range:NSMakeRange(0, str.length)];
    
    iRonBarrageModel *m = [[iRonBarrageModel alloc] initWithBarrageContent:attr];
    m.displayLocation = _manager.displayLocation;
    m.direction       = _manager.scrollDirection;
    m.object = [UIImage imageNamed:[NSString stringWithFormat:@"digg_%d",arc4random() % 10]];
    return m;
}
</code></pre>

## 原理-Principle



</p>
