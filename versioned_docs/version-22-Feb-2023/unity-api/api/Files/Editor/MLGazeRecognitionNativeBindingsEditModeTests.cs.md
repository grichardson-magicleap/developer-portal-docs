---

title: MLGazeRecognitionNativeBindingsEditModeTests.cs

---


# MLGazeRecognitionNativeBindingsEditModeTests.cs









## Source code

```csharp
using System.Reflection;
using NUnit.Framework;

namespace Tests.Editor
{
    public class MLGazeRecognitionNativeBindingsEditModeTests : NativeBindingsTests
    {
        [SetUp]
        public void SetupNativeBindings()
        {
            var apiType = typeof(UnityEngine.XR.MagicLeap.MLGazeRecognition);
            nativeBindings = apiType.GetNestedType("NativeBindings", BindingFlags.NonPublic);
        }

        [Test]
        public void NativeBinding_MLGazeRecognitionCreate_Exists()
        {
            AssertThatMethodExists("MLGazeRecognitionCreate");
        }

        [Test]
        public void NativeBinding_MLGazeRecognitionDestroy_Exists()
        {
            AssertThatMethodExists("MLGazeRecognitionDestroy");
        }

        [Test]
        public void NativeBinding_MLGazeRecognitionGetState_Exists()
        {
            AssertThatMethodExists("MLGazeRecognitionGetState");
        }

        [Test]
        public void NativeBinding_MLGazeRecognitionGetStaticData_Exists()
        {
            AssertThatMethodExists("MLGazeRecognitionGetStaticData");
        }
    }
}
```




