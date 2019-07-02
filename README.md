# BasePlayground
Basic Playground Setup with all screen size. It's very usefull to test UI quickly with a basic file that already contains all screens size. You can clone or download the file in the repository or just copy and paste the code lines below in your own playground file.

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

### Note: The resolution is transform into logical resolution to fit with Apple's points system(@x1/@x2/@x3) and to avoid LiveView errors.
### Note: The testUI() func is called from the init method of the PlaygroundViewController and not from the @override loadView() to avoid LiveView infinite loading loop.
