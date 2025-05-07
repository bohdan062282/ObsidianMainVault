## Resources.Load
### Declaration
`public static T Load(string path);`
### Parameters

|   |   |
|---|---|
|path|Path to the target resource to load.|

### Returns

**T** An object of the requested generic parameter type.
### Description

Loads the asset of the requested type stored at `path` in a [Resources](https://docs.unity3d.com/6000.0/Documentation/ScriptReference/Resources.html) folder using a generic parameter type filter of type `T`.
### Example
//Load a text file (Assets/[Resources](https://docs.unity3d.com/6000.0/Documentation/ScriptReference/Resources.html)/Text/textFile01.txt)
var textFile = [Resources.Load](https://docs.unity3d.com/6000.0/Documentation/ScriptReference/Resources.Load.html)<[TextAsset](https://docs.unity3d.com/6000.0/Documentation/ScriptReference/TextAsset.html)>("Text/textFile01");
