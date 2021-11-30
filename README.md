## HQ ltv.

#### Integration steps:

1. Add `hqsdk` repository to `/<project_path>/build.gradle`:

```groovy
allprojects {
    repositories {
        google()
        mavenCentral()
        
        maven { url 'https://repo.repsy.io/mvn/humanteq/hqsdk' }
    }
```
2. Add `hqm-core` dependency to `/<project_path>/app/build.gradle`:

```groovy
dependencies {    
    implementation 'io.humanteq.hqm:hqm-ltv:1.0.0'
}
```

3. Sync project and initialize SDK:

(Kotlin)

```kotlin
class App : Application() {

    override fun onCreate() {
        super.onCreate()

        // Init
        HQSdk.init(this, "your_api_key", BuildConfig.DEBUG)

        // Send ad income event
        HQSdk.adIncome()
        
        // Send ad income event with additional data
        HQSdk.adIncome(mapOf(
                Pair("test_param1", "test_value1"),
                Pair("test_param2", "test_value2")
        ))
    }
}
```

(Java)

```java
public class App extends Application {
    
    @Override
    public void onCreate() {
        super.onCreate();

        // Init
        HQSdk.init(this, "your_api_key", BuildConfig.DEBUG);

        // Send ad income event
        HQSdk.adIncome();

        // Send ad income event with additional data
        HQSdk.adIncome(new HashMap<>(){{
            put("test_param1", "test_value1");
        }});
    }
}
```
<br>

#### Unity integration:

Unity package: [hqm_ltv_1.0.0.unitypackage](https://github.com/HumanteQ/hqm_ltv/raw/master/hqm_ltv_1.0.0.unitypackage)

#### Integration instructions:

1. Install [Play Services Resolver](https://github.com/googlesamples/unity-jar-resolver/)
2. Download and import [hqm_ltv_1.0.0.unitypackage](https://github.com/HumanteQ/hqm_ltv/raw/master/hqm_ltv_1.0.0.unitypackage)
3. Initialize SDK:

```csharp
            ...
            
            // Init SDK
            HQSdk.Init(
                "hqm_api_key",     // your api key
                true);             // is debug enabled
  ```
4. Send ad income event:

```csharp
            ...
            
            // Empty Ad income event
            HQSdk.AdIncome();
            
            // Empty Ad income event with additional params
            Dictionary<string, string> map = new Dictionary<string, string>();
            map["test1"] = "test_value1";
            map["test2"] = "test_value2";
            
            HQSdk.AdIncome(map);
  ```