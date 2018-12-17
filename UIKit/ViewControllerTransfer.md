UITabBarController-以下简称TBC
UINavigationController-以下简称NVC

VC分类：  
1.Container View Controller(parentVC)：TBC NVC (Page/Split……)+某些自定义的ContainerVC(比如汉堡的侧滑Controller)  
2.Content View Controller(childVC)：业务层的某个XXTableViewController,XXCollectionViewController  

VC的切换：  
1.从parentVC 切换到parentVC(TBC嵌套NVC,点tabBarButton，切换NVC；；；present一个NVC)  
2.parentVC切换自己的childVC（设置RootVC） 
3.childVC 让 parentVC 切换到 其他的ContentVC（NVC的push/pop）  
4.childVC 让 parentVC 切换到 其他的ContainerVC（self.navigationController present: XXXNavigationController)  
5.增加临时的window来让新的vc显示在最前面  
