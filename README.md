# DrawerNavigatorExample
*Reference:* https://aboutreact.com/react-native-navigation-drawer/

## Note
Applied patch from https://stackoverflow.com/questions/53394982/react-navigation-swipe-on-drawer-does-not-work-in-android 
to fix a gesture handling bug for Android:

```
// MainActivity.java
import com.facebook.react.ReactActivity;
+ import com.facebook.react.ReactActivityDelegate;
+ import com.facebook.react.ReactRootView;
+ import com.swmansion.gesturehandler.react.RNGestureHandlerEnabledRootView;

public class MainActivity extends ReactActivity {

  @Override
  protected String getMainComponentName() {
    return "Example";
  }

+  @Override
+  protected ReactActivityDelegate createReactActivityDelegate() {
+    return new ReactActivityDelegate(this, getMainComponentName()) {
+      @Override
+      protected ReactRootView createRootView() {
+       return new RNGestureHandlerEnabledRootView(MainActivity.this);
+      }
+    };
+  }
}
```
