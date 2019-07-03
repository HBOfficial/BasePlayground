# BasePlayground
Basic Playground Setup with all screen size and type. The playground is working very well for testing quickly small label, button, and imageview, but when we are trying to simulate an entire view with an high resolution, some problems occuring with the aspect ratio, the width and the height of the playground simulation. As far as i know, it seems like the playground can't generate an high resolution view like if it was shrink to fit(But new Iphones and Ipads require it). This is why this playground is downscaling the real size and aspect ratio with something smaller. You can clone or download the file in the repository or just copy and paste the code lines below in your own playground file/project.

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




