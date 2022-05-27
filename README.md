LocationManager
=====================

Location manager is a CLLocationManager wrapper written entirely in Swift
----------------------------------

#### Podfile

To integrate VMLocationManager into your Xcode project using CocoaPods, specify it in your `Podfile`:

```ruby
source 'https://github.com/CocoaPods/Specs.git'
platform :ios, '12.0'

target 'TargetName' do
pod 'VMLocationManager', '~> 1.0.0'
end
```

Then, run the following command:

```bash
$ pod install
```

Usage
-----------
***Closure***

**Location update**

    var locationManager = LocationManager.sharedInstance
            locationManager.showVerboseMessage = true
            locationManager.autoUpdate = false
            locationManager.startUpdatingLocationWithCompletionHandler { (latitude, longitude, status, verboseMessage, error) -> () in
                
                println("lat:\(latitude) lon:\(longitude) status:\(status) error:\(error)")
                
                println(verboseMessage)
                
            }

**Geocoding using Apple service**

 

    var locationManager = LocationManager.sharedInstance
            
    locationManager.geocodeAddressString(address: "Apple Inc., Infinite Loop, Cupertino, CA  95014, United States") { (geocodeInfo,placemark,error) -> Void in
                
                if(error != nil){
                    
                    println(error)
                }else{
                    
                    println(geocodeInfo!)
                }
            }
            

**Reverse Geocoding using Apple service**

    var locationManager = LocationManager.sharedInstance
                locationManager.reverseGeocodeLocationWithLatLon(latitude: 37.331789, longitude: -122.029620) { (reverseGecodeInfo,placemark,error) -> Void in
                
                if(error != nil){
                    
                    println(error)
                }else{
                    
                    println(reverseGecodeInfo!)
                }
                
            }

**Geocoding using Google service**

    var locationManager = LocationManager.sharedInstance
       locationManager.geocodeUsingGoogleAddressString(address: "Apple Inc., Infinite Loop, Cupertino, CA  95014, United States") { (geocodeInfo,placemark,error) -> Void in
                
                if(error != nil){
                    
                    println(error)
                }else{
                    
                    println(geocodeInfo!)
                }
                
            }


**Reverse Geocoding using Google service**

    var locationManager = LocationManager.sharedInstance
          locationManager.reverseGeocodeLocationUsingGoogleWithLatLon(latitude: 37.331789, longitude: -122.029620) { (reverseGecodeInfo,placemark,error) -> Void in
                
                if(error != nil){
                    
                    println(error)
                }else{
                    
                    println(reverseGecodeInfo!)
                }
            }

----------

***Delegate***

**Location update**

    *class ViewController: UIViewController ,LocationManagerDelegate{....*
    
    override func viewDidLoad() {
        
        super.viewDidLoad()
        
        var locationManager = LocationManager.sharedInstance
        
        locationManager.delegate = self
        
        locationManager.startUpdatingLocation()
        
        locationManager.stopUpdatingLocation()
    }
    
     func locationManagerStatus(status:NSString){
        
        println(status)
    }
    
    
    func locationManagerReceivedError(error:NSString){
        
        println(error)
        
    }
    
    func locationFoundGetAsString(latitude: NSString, longitude: NSString) {
       
    }
    
    
    func locationFound(latitude:Double, longitude:Double){
        
    }
