---
title: Extensions

---

# Extensions










## Public Methods

### bool TryGetEyeTrackingState {#bool-trygeteyetrackingstate}

Try to get the [InputSubsystem.Extensions.MLEyes.State](/versioned_docs/version-22-Feb-2023/unity-api/api/UnityEngine.XR.MagicLeap/InputSubsystem/Extensions/MLEyes/UnityEngine.XR.MagicLeap.InputSubsystem.Extensions.MLEyes.State.md), InputDevice   from the given . 

```csharp
public static bool TryGetEyeTrackingState(
    InputDevice eyesDevice,
    out MLEyes.State state
)
```


**Parameters**

| Type | Name  | Description  | 
|--|--|--|
| InputDevice |eyesDevice|The eye tracking device|
| out [MLEyes.State](/versioned_docs/version-22-Feb-2023/unity-api/api/UnityEngine.XR.MagicLeap/InputSubsystem/Extensions/MLEyes/UnityEngine.XR.MagicLeap.InputSubsystem.Extensions.MLEyes.State.md) |state|The resulting Eye State|


**Details**



This method expects that a Magic Leap Eye Tracking input device is used in query. (ie. has the EyeTracking 
.) Note, you can retrieve Magic Leap devices with specific characteristics using the  method. Once an eye tracking device is found and  is equal to true, you can get the  and access device specific features such as . For example: 

```cpp
InputDevice eyesDevice = InputSubsystem.Utils.FindMagicLeapDevice(InputDeviceCharacteristics.EyeTracking | InputDeviceCharacteristics.TrackedDevice);
if(eyesDevice.isValid){
    InputSubsystem.Extensions.TryGetEyeTrackingState(eyesDevice, out MLEyes.State trackingState);
    if(trackingState.FixationConfidence){
        Debug.Log("FixationConfidence " + trackingState.FixationConfidence);
    }
}
```



**See**: InputDeviceCharacteristics, [InputSubsystem.Utils.FindMagicLeapDevice](/versioned_docs/version-22-Feb-2023/unity-api/api/UnityEngine.XR.MagicLeap/InputSubsystem/UnityEngine.XR.MagicLeap.InputSubsystem.Utils.md#inputdevice-findmagicleapdevice), InputDevice.isValid, [MLEyes.State](/versioned_docs/version-22-Feb-2023/unity-api/api/UnityEngine.XR.MagicLeap/InputSubsystem/Extensions/MLEyes/UnityEngine.XR.MagicLeap.InputSubsystem.Extensions.MLEyes.State.md), [InputSubsystem.Extensions.MLEyes.State.FixationConfidence](/versioned_docs/version-22-Feb-2023/unity-api/api/UnityEngine.XR.MagicLeap/InputSubsystem/Extensions/MLEyes/UnityEngine.XR.MagicLeap.InputSubsystem.Extensions.MLEyes.State.md#readonly-float-fixationconfidence)



**Returns**: True if the resulting [InputSubsystem.Extensions.MLEyes.State](/versioned_docs/version-22-Feb-2023/unity-api/api/UnityEngine.XR.MagicLeap/InputSubsystem/Extensions/MLEyes/UnityEngine.XR.MagicLeap.InputSubsystem.Extensions.MLEyes.State.md)


is valid. 



-----------

### bool TryGetHeadTrackingState {#bool-trygetheadtrackingstate}

```csharp
public static bool TryGetHeadTrackingState(
    InputDevice headDevice,
    out MLHeadTracking.State headTrackingState
)
```


**Parameters**

| Type | Name  | Description  | 
|--|--|--|
| InputDevice |headDevice||
| out [MLHeadTracking.State](/versioned_docs/version-22-Feb-2023/unity-api/api/UnityEngine.XR.MagicLeap/InputSubsystem/Extensions/MLHeadTracking/UnityEngine.XR.MagicLeap.InputSubsystem.Extensions.MLHeadTracking.State.md) |headTrackingState|A structure containing information on the current state of the Head Tracking system. |






-----------


