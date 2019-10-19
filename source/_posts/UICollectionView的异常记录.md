---
title: UICollectionView的异常记录
date: 2019-10-19 22:22:10
tags:
- UICollectionView
- crash
- setSizeHasBeenSet
---

## UICollectionView的异常记录

同事在使用UICollectionView时，碰到iOS10的真机上出现crash异常，花了一点时间定位问题后，发现是UICollectionView中的UICollectionViewDelegateFlowLayout回调方法的问题，可能是Apple的bug（iOS12上没有碰到），不过我感觉主要还是控件理解不够透彻的关系，使用不够规范，不然应该可以避开或者绕过。


```
- (CGSize)collectionView:(UICollectionView *)collectionView
                  layout:(UICollectionViewLayout *)collectionViewLayout
  sizeForItemAtIndexPath:(NSIndexPath *)indexPath
```

在上面这个计算cell大小的方法中，调用了[collectionView dequeueReusableCellWithReuseIdentifier:identifier forIndexPath:indexPath]方法。


### 问题表现

#### A-在iOS10的真机上出现下面的异常：
```
reason: '-[NSCFString setSizeHasBeenSet:]: unrecognized selector sent to instance 0x610000076bc0' 
*** First throw call stack: 
(
 0 CoreFoundation 0x0000000109dd9d4b __exceptionPreprocess + 171
 1 libobjc.A.dylib 0x00000001094d921e objc_exception_throw + 48
 2 CoreFoundation 0x0000000109e49f04 -[NSObject(NSObject) doesNotRecognizeSelector:] + 132 
 3 CoreFoundation 0x0000000109d5f005 ___forwarding_ + 1013 
 4 CoreFoundation 0x0000000109d5eb88 _CF_forwarding_prep_0 + 120 
 5 UIKit 0x00000001080d9485 -[UICollectionViewFlowLayout _getSizingInfosWithExistingSizingDictionary:] + 3691 
 6 UIKit 0x00000001080da97b -[UICollectionViewFlowLayout _fetchItemsInfoForRect:] + 127 
 7 UIKit 0x00000001080d3504 -[UICollectionViewFlowLayout prepareLayout] + 273 
 8 UIKit 0x00000001080f3d6c -[UICollectionViewData _prepareToLoadData] + 159 
 9 UIKit 0x00000001080f4618 -[UICollectionViewData validateLayoutInRect:] + 57 
 10 UIKit 0x000000010809b6d4 -[UICollectionView layoutSubviews] + 232 
 11 UIKit 0x0000000107817ab8 -[UIView(CALayerDelegate) layoutSublayersOfLayer:] + 1237 
 12 QuartzCore 0x0000000106fcdbf8 -[CALayer layoutSublayers] + 146 
 13 QuartzCore 0x0000000106fc1440 _ZN2CA5Layer16layout_if_neededEPNS_11TransactionE + 366 
 14 QuartzCore 0x0000000106fc12be _ZN2CA5Layer28layout_and_display_if_neededEPNS_11TransactionE + 24 
 15 QuartzCore 0x0000000106f4f318 _ZN2CA7Context18commit_transactionEPNS_11TransactionE + 280 
 16 QuartzCore 0x0000000106f7c3ff _ZN2CA11Transaction6commitEv + 475 
 17 QuartzCore 0x0000000106f7cd6f _ZN2CA11Transaction17observer_callbackEP19__CFRunLoopObservermPv + 113 
 18 CoreFoundation 0x0000000109d7e267 CFRUNLOOP_IS_CALLING_OUT_TO_AN_OBSERVER_CALLBACK_FUNCTION + 23 
 19 CoreFoundation 0x0000000109d7e1d7 __CFRunLoopDoObservers + 391 
 20 CoreFoundation 0x0000000109d628a6 CFRunLoopRunSpecific + 454 
 21 UIKit 0x000000010774caea -[UIApplication _run] + 434 
 22 UIKit 0x0000000107752c68 UIApplicationMain + 159 
 23 Moden 0x0000000104ab4fbf main + 111 
 24 libdyld.dylib 0x000000010ad4e68d start + 1 
) libc++abi.dylib: terminating with uncaught exception of type NSException 
(lldb)
```


#### B-在iOS9、iOS10的模拟器上出现下面的异常：

```
2019-10-19 23:02:29.148 UICollectionViewDemo[20163:418963] *** Terminating app due to uncaught exception 'NSRangeException', reason: '*** -[__NSArrayM objectAtIndex:]: index 1 beyond bounds [0 .. 0]'
*** First throw call stack:
(
	0   CoreFoundation                      0x00000001075f534b __exceptionPreprocess + 171
	1   libobjc.A.dylib                     0x000000010705621e objc_exception_throw + 48
	2   CoreFoundation                      0x0000000107526f1b -[__NSArrayM objectAtIndex:] + 203
	3   UIKit                               0x0000000108ab2fcd -[UICollectionViewFlowLayout _getSizingInfosWithExistingSizingDictionary:] + 1623
	4   UIKit                               0x0000000108ab4cd7 -[UICollectionViewFlowLayout _fetchItemsInfoForRect:] + 127
	5   UIKit                               0x0000000108aad860 -[UICollectionViewFlowLayout prepareLayout] + 273
	6   UIKit                               0x0000000108ace0c8 -[UICollectionViewData _prepareToLoadData] + 159
	7   UIKit                               0x0000000108ad11d5 -[UICollectionViewData layoutAttributesForItemAtIndexPath:] + 39
	8   UIKit                               0x0000000108a7f1b3 -[UICollectionView _dequeueReusableViewOfKind:withIdentifier:forIndexPath:viewCategory:] + 384
	9   UIKit                               0x0000000108a7fc84 -[UICollectionView dequeueReusableCellWithReuseIdentifier:forIndexPath:] + 169
	10  UICollectionViewDemo                0x0000000106a7c798 -[ViewController collectionView:cellForItemAtIndexPath:] + 104
	11  UICollectionViewDemo                0x0000000106a7c9ff -[ViewController collectionView:layout:sizeForItemAtIndexPath:] + 143
	12  UIKit                               0x0000000108ab354f -[UICollectionViewFlowLayout _getSizingInfosWithExistingSizingDictionary:] + 3033
	13  UIKit                               0x0000000108ab4cd7 -[UICollectionViewFlowLayout _fetchItemsInfoForRect:] + 127
	14  UIKit                               0x0000000108aad860 -[UICollectionViewFlowLayout prepareLayout] + 273
	15  UIKit                               0x0000000108ace0c8 -[UICollectionViewData _prepareToLoadData] + 159
	16  UIKit                               0x0000000108ace974 -[UICollectionViewData validateLayoutInRect:] + 57
	17  UIKit                               0x0000000108a75d12 -[UICollectionView layoutSubviews] + 232
	18  UIKit                               0x00000001081ed344 -[UIView(CALayerDelegate) layoutSublayersOfLayer:] + 1237
	19  QuartzCore                          0x000000010d23bcdc -[CALayer layoutSublayers] + 146
	20  QuartzCore                          0x000000010d22f7a0 _ZN2CA5Layer16layout_if_neededEPNS_11TransactionE + 366
	21  QuartzCore                          0x000000010d22f61e _ZN2CA5Layer28layout_and_display_if_neededEPNS_11TransactionE + 24
	22  QuartzCore                          0x000000010d1bd62c _ZN2CA7Context18commit_transactionEPNS_11TransactionE + 280
	23  QuartzCore                          0x000000010d1ea713 _ZN2CA11Transaction6commitEv + 475
	24  QuartzCore                          0x000000010d1eb083 _ZN2CA11Transaction17observer_callbackEP19__CFRunLoopObservermPv + 113
	25  CoreFoundation                      0x0000000107599e17 __CFRUNLOOP_IS_CALLING_OUT_TO_AN_OBSERVER_CALLBACK_FUNCTION__ + 23
	26  CoreFoundation                      0x0000000107599d87 __CFRunLoopDoObservers + 391
	27  CoreFoundation                      0x000000010757e4b6 CFRunLoopRunSpecific + 454
	28  UIKit                               0x0000000108122db6 -[UIApplication _run] + 434
	29  UIKit                               0x0000000108128f34 UIApplicationMain + 159
	30  UICollectionViewDemo                0x0000000106a7cc10 main + 112
	31  libdyld.dylib                       0x000000010aae068d start + 1
)
libc++abi.dylib: terminating with uncaught exception of type NSException
(lldb) 
```

### 问题处理方案
```
- (CGSize)collectionView:(UICollectionView *)collectionView
                  layout:(UICollectionViewLayout *)collectionViewLayout
  sizeForItemAtIndexPath:(NSIndexPath *)indexPath
{
    //测试1
//    RHCollectionViewCell *cell = (RHCollectionViewCell *)[self collectionView:collectionView cellForItemAtIndexPath:indexPath];
    //测试2
    static NSString *identifier = @"CellIdentifier";
    RHCollectionViewCell *cell = (RHCollectionViewCell *)[collectionView dequeueReusableCellWithReuseIdentifier:identifier forIndexPath:indexPath];
    //测试3
//    RHCollectionViewCell *cell = [[RHCollectionViewCell alloc] init];
    return [cell sizeOfCell];
    
//    return CGSizeZero;
}
```
<mark>**从上面的测试中，1和2在iOS10的模拟器上都出现了上面B中的异常，最后直接通过计算size来解决问题。**</mark>


### 问题参考
* [UICollectionView sizeForItemAt IndexPath](https://stackoverflow.com/questions/43955143/uicollectionview-sizeforitemat-indexpath)
* [UICollectionView - dynamic cell height? [duplicate]](https://stackoverflow.com/questions/28161839/uicollectionview-dynamic-cell-height/53786943#53786943)