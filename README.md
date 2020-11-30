# mobile_number

This is a FLutter Plugin to get the device mobile number.
#### Note: It works for Android only because getting mobile number of sim card is not supported in iOS.
#### Note: If the mobile number is not pre-exist on sim card it will not return te phone number.

## Installation 
#### Link on Flutter plugins
https://pub.dev/packages/mobile_number

#### Note: 
if you still using depecated FlutterActivty on MainActivity.java
which is import of 
- `import io.flutter.app.FlutterActivity;`

not 
- `import io.flutter.embedding.android.FlutterActivity;`

then you need to add the following to your MainActivity.java
``` 
@Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        MobileNumberPlugin.registerWith(registrarFor("com.amorenew.mobile_number.MobileNumberPlugin()"));
    }
  ```

## Usage

#### Check Phone Permission

```await MobileNumber.hasPhonePermission```

#### Request Phone Permission

```await MobileNumber.requestPhonePermission```

#### Listen to widget resume after Phone Permission request

```MobileNumber.listenPhonePermission((isPermissionGranted) {
      if (isPermissionGranted) {
        //Get mobile number
      } else {
        //Request Phone Permission
      }
    });
  ```

#### Get first sim card number

```Future<String> getMobileNumber() async {
    final String mobileNumber = await MobileNumber.mobileNumber;
    return mobileNumber;
  }
  ```

#### Get List of sim cards for dual sim cards

```Future<List<SimCard>> geSimCards() async {
    final List<SimCard> simCards = await MobileNumber.getSimCards;
    return simCards;
  }
  ```
  

![alt text](https://raw.githubusercontent.com/amorenew/Flutter-Mobile-Number-Plugin/master/sample1.png)
