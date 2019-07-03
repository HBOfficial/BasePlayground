# BasePlayground
Basic Playground Setup with all screen size and type. The playground is working very well for testing quickly small label, button, and imageview, **but when we are trying to simulate an entire view with an high resolution, some problems occuring with the aspect ratio, the width and the height of the playground simulation**. **_As far as i know, it seems like the playground can't generate an high resolution view like if it was shrink to fit(But new Iphones and Ipads require it)_**. This is why this playground is downscaling the real size and aspect ratio with something smaller. You can clone or download the file in the repository or just copy and paste the code lines below in your own playground file/project.

# How it works
To test your UI on a specific device, you just need to specify the device and the orientation you need in the testUI() func:
```self.preferredContentSizeWithDevice(device: .IphoneXr, isLandscape: false)```

If you are working with multiple UI, just uncomments the code below, it will automatically switch the deviceType from the device you specified above:
```
/*
         switch deviceType! {
         
         case .iphone:
         //Do some stuff for iphone
         print("Iphone spoted")
         break
         
         case .ipad:
         //Do some stuff for ipad
         print("Ipad spoted")
         break
         
         case .watch:
         //Do some stuff for watch
         print("Watch spoted")
         break
         
         }
         */ 
```

### Note: The resolution is transform into logical resolution to fit with Apple's points system(@x2/@x3), and then is downscale to avoid LiveView errors.
### Note: The testUI() func is called from the init method of the PlaygroundViewController and not from the @override loadView() to avoid LiveView infinite loading loop.

# Important
**If you want to deal with a constant size in float points(like label font size or constraint position), you will need to transform the size you want to test with the pgFit function:**
```
viewExample.bottomAnchor.constraint(equalTo: self.view.bottomAnchor, constant: pgFit(float: -50)).isActive = true
```

**When you need to import your code into your project, just replace the pgFit function call with your Cgfloat value:**
```
viewExample.bottomAnchor.constraint(equalTo: self.view.bottomAnchor, constant: -50).isActive = true
```

# PlaygroundViewController
```
//  PlaygroundViewController.playground
//
//  Created by Hélie de Bernis on 01/07/2019.



import UIKit
import PlaygroundSupport



class PlaygroundViewController: UIViewController {
    
    var deviceType: DeviceType?
    
    init() {
        super.init(nibName: nil, bundle: .main)
        self.testUI()
        
        
    }
    
    required init?(coder aDecoder: NSCoder) {
        fatalError("init(coder:) has not been implemented")
    }
    
    
    
    //Modify the size of the LiveViewPage with the DeviceScreen you specify
    //Note: Resolution is transform into logical resolution(@x2/@x3), and then downscale to avoid Liveview errors
    func preferredContentSizeWithDevice(device: DeviceScreen, isLandscape: Bool) {
        
        switch device {
            
        case .Iphone4s:
            self.deviceType = .iphone
            if isLandscape {
                self.preferredContentSize = CGSize(width: (960/2)*0.7, height: (640/2)*0.7)
            }else{
                self.preferredContentSize = CGSize(width: (640/2)*0.7, height: (960/2)*0.7)
            }
            break
        case .Iphone5_5s_5SE:
            self.deviceType = .iphone
            if isLandscape {
                self.preferredContentSize = CGSize(width: (1136/2)*0.7, height: (640/2)*0.7)
            }else{
                self.preferredContentSize = CGSize(width: (640/2)*0.7, height: (1136/2)*0.7)
            }
            break
        case .Iphone6_7_8:
            self.deviceType = .iphone
            if isLandscape {
                self.preferredContentSize = CGSize(width: (1334/2)*0.7, height: (750/2)*0.7)
            }else{
                self.preferredContentSize = CGSize(width: (750/2)*0.7, height: (1334/2)*0.7)
            }
            break
        case .Iphone6_7_8_Plus:
            self.deviceType = .iphone
            if isLandscape {
                self.preferredContentSize = CGSize(width: (2208/3)*0.7, height: (1242/3)*0.7)
            }else{
                self.preferredContentSize = CGSize(width: (1242/3)*0.7, height: (2208/3)*0.7)
            }
            break
        case .IphoneXr:
            self.deviceType = .iphone
            if isLandscape {
                self.preferredContentSize = CGSize(width: (1792/2)*0.7, height: (828/2)*0.7)
            }else{
                self.preferredContentSize = CGSize(width: (828/2)*0.7, height: (1792/2)*0.7)
            }
            break
        case .IphoneX_Xs:
            self.deviceType = .iphone
            if isLandscape {
                self.preferredContentSize = CGSize(width: (2436/3)*0.7, height: (1125/3)*0.7)
            }else{
                self.preferredContentSize = CGSize(width: (1125/3)*0.7, height: (2436/3)*0.7)
            }
            break
        case .IphoneXsMax:
            self.deviceType = .iphone
            if isLandscape {
                self.preferredContentSize = CGSize(width: (2688/3)*0.7, height: (1242/3)*0.7)
            }else{
                self.preferredContentSize = CGSize(width: (1242/3)*0.7, height: (2688/3)*0.7)
            }
            break
            
        case .IpadMini2_3_4:
            self.deviceType = .ipad
            if isLandscape {
                self.preferredContentSize = CGSize(width: (2048/2)*0.5, height: (1536/2)*0.5)
            }else{
                self.preferredContentSize = CGSize(width: (1536/2)*0.5, height: (2048/2)*0.5)
            }
            break
        case .IpadAir3_4_97i:
            self.deviceType = .ipad
            if isLandscape {
                self.preferredContentSize = CGSize(width: (2048/2)*0.5, height: (1536/2)*0.5)
            }else{
                self.preferredContentSize = CGSize(width: (1536/2)*0.5, height: (2048/2)*0.5)
            }
            break
        case .IpadPro105i:
            self.deviceType = .ipad
            if isLandscape {
                self.preferredContentSize = CGSize(width: (2224/2)*0.5, height: (1668/2)*0.5)
            }else{
                self.preferredContentSize = CGSize(width: (1668/2)*0.5, height: (2224/2)*0.5)
            }
            break
        case .IpadPro110i:
            self.deviceType = .ipad
            if isLandscape {
                self.preferredContentSize = CGSize(width: (2388/2)*0.5, height: (1668/2)*0.5)
            }else{
                self.preferredContentSize = CGSize(width: (1668/2)*0.5, height: (2388/2)*0.5)
            }
            break
        case .IpadPro129i:
            self.deviceType = .ipad
            if isLandscape {
                self.preferredContentSize = CGSize(width: (2732/2)*0.5, height: (2048/2)*0.5)
            }else{
                self.preferredContentSize = CGSize(width: (2048/2)*0.5, height: (2732/2)*0.5)
            }
            break
            
        case .WatchSeries1_2_3_38mm:
            self.deviceType = .watch
            self.preferredContentSize = CGSize(width: 272/2, height: 340/2)
            break
        case .WatchSeries1_2_3_42mm:
            self.deviceType = .watch
            self.preferredContentSize = CGSize(width: 312/2, height: 390/2)
            break
        case .WatchSeries4_40mm:
            self.deviceType = .watch
            self.preferredContentSize = CGSize(width: 324/2, height: 394/2)
            break
        case .WatchSeries4_44mm:
            self.deviceType = .watch
            self.preferredContentSize = CGSize(width: 368/2, height: 448/2)
            break
            
            
        }
        
    }
    
    //Enum of all Devices
    enum DeviceScreen: String {
        
        case Iphone4s,Iphone5_5s_5SE,Iphone6_7_8,Iphone6_7_8_Plus,IphoneXr,IphoneX_Xs,IphoneXsMax,IpadMini2_3_4,IpadAir3_4_97i,IpadPro105i,IpadPro110i,IpadPro129i, WatchSeries1_2_3_38mm,WatchSeries1_2_3_42mm,WatchSeries4_40mm,WatchSeries4_44mm
        
        
    }
    //Enum of Device Type
    enum DeviceType {
        case ipad,iphone,watch
    }
    
    //Downscale points into playground points
    func pgFit(float:CGFloat) -> CGFloat {
        
        switch deviceType! {
        case .iphone:
            return float*0.7
        case .ipad:
            return float*0.5
        case .watch:
            return float
            
        }
        
        
    }
    
    
    
    //Just switch the device you want to test here, and specify the device orientation
    //NOTE: DeviceOrientation have no effect on Watch
    func testUI(){
        
        //Fit playground with device size
        self.preferredContentSizeWithDevice(device: .IphoneXr, isLandscape: false)
        //Sync the view of the PlaygroundViewcontroller with the preferredContentSize
        self.view.frame = CGRect(x: 0, y: 0, width: self.preferredContentSize.width, height: self.preferredContentSize.height)
        self.view.backgroundColor = .white
        
        //Write and test your UI here
        
        /*
         
         let viewExample = UIView()
         
         viewExample.backgroundColor = .blue
         self.view.addSubview(viewExample)
         
         viewExample.translatesAutoresizingMaskIntoConstraints = false
         viewExample.topAnchor.constraint(equalTo: self.view.topAnchor).isActive = true
         viewExample.bottomAnchor.constraint(equalTo: self.view.bottomAnchor, constant: pgFit(float: -50)).isActive = true
         viewExample.leftAnchor.constraint(equalTo: self.view.leftAnchor).isActive = true
         viewExample.rightAnchor.constraint(equalTo: self.view.rightAnchor).isActive = true
         
         */
        
        
        //NOTE: For multiple UI, uncomments the next lines, it will automatically switch the deviceType
        //from the device you specified above
        /*
         switch deviceType! {
         
         case .iphone:
         //Do some stuff for iphone
         print("Iphone spoted")
         break
         
         case .ipad:
         //Do some stuff for ipad
         print("Ipad spoted")
         break
         
         case .watch:
         //Do some stuff for watch
         print("Watch spoted")
         break
         
         }
         
         */
        
        
    }
    
    
    
    
}

//Sync the current LiveView with the PlaygroundViewController
PlaygroundPage.current.liveView = PlaygroundViewController()
```

# Enjoy !








