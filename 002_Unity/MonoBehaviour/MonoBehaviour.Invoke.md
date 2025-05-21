## Declaration

public void Invoke(string methodName, float time);

### Description

Invokes the method `methodName` in time seconds.

If time is set to 0 and Invoke is called before the first frame update, the method is invoked at the next Update cycle before [MonoBehaviour.Update](https://docs.unity3d.com/6000.0/Documentation/ScriptReference/MonoBehaviour.Update.html). In this case, it's better to call the function directly.  
  
Note: Setting time to negative values is identical to setting it to 0.  
  
In other cases, the order of execution of the method depends on the timing of the invocation.  
  
If you need to pass parameters to your method, consider using [Coroutine](https://docs.unity3d.com/6000.0/Documentation/ScriptReference/Coroutine.html) instead. Coroutines also provide better performance.