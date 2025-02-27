---
id: soundfield-components
title: Soundfield Components
sidebar_position: 1
description: Detailed descriptions and screenshots of all available components of Soundfield Audio
date: 09/10/2022
tags: [Unity, Walkthroughs, Audio, MSA, Soundfield]
keywords: [Unity,Audio, MSA, Soundfield]
---

# Soundfield Components

## ML Listener

Extends Unity's AudioListener features by introducing additional parameters related to global spatialization. The MSAListener component has settings for global reverb and transmission properties.

![MSAListener component settings](/img/unity/enable_acoustic_map.png)

**Enable Acoustic Map**: Acoustic Map data is a device-curated representation of the acoustics of the local physical environment. Enabling the Acoustic Map makes virtual objects sound as though they exist in the local environment.

**Indirect Sound Obstructions**: Enables/Disables the indirect sound obstruction.

**Defaults**:  These define the default values for each parameter.

**Transmission Properties**: Default values for Transmission:

![MSAListener component settings](/img/unity/ml-listener-2.png)

Transmission is specified using `MultibandLevelProperties`, which includes gain and 3-band EQ. The values [0dB, (0dB, 0dB, 0dB)] represents fully transmissive while [-96dB, (0dB, 0dB, 0dB)] or [0dB, (-96dB, -96dB, -96dB)] represents fully obstructed.

**Dispersion Properties**: Default values for Dispersion:

![MSAListener component settings](/img/unity/ml-listener-3.png)

- **Gain**: Dispersion output mix level.
  - **Main**: Level for all freqs.
  - **LF**: Level for low freqs.
  - **MF**: Level for mid freqs.
  - **HF**: Level for high freqs.
- **Pre Delay**: Delay (secs) from direct sound to earliest reflection cluster onset.

**Reverb Properties**: Default values for Reverb:

![MSAListener component settings](/img/unity/ml-listener-4.png)

- **Gain**: Reverb output mix level.
  - **Main**: Level for all freqs.
  - **LF**: Level for low freqs.
  - **MF**: Level for mid freqs.
  - **HF**: Level for high freqs.
- **Pre Delay**: Delay (secs) from direct sound to the late reverberation onset.
- **Decay Time**: Decay time (secs) for late reverberation.
- **Decay Time LF Ratio**: Relative reverberation decay time multiplying factor for low frequencies.
- **Decay Time HF Ratio**: Relative reverberation decay time multiplying factor for high frequencies.

### Auto-Instantiation
A typical Unity scene will always have an `MLListener` component present that will be responsible for servicing and outputting the binaural audio for all the `MLPointSource` components that are present. However, this approach makes it difficult to handle dynamic loading or unloading of multiple scenes both during editing and at runtime.

`MLListener` provides a mechanism to ensure that when an `MLPointSource` is spawned in a scene an `MLListener` component will always be present in order to ensure the source is supported.

#### Additive Scene Loading

While it is needed to hear sound from an `MLPointSource`, adding another `MLListener` component to any additively loaded scene will cause your build to fail at runtime.

To solve this, an `MLListener` component is instantiated automatically at runtime to temporarily support the `MLPointsource` components in the current scene. This temporary instantiation will not be included when the scene is saved in order to prevent more than one `MLListener` component from existing simultaneously in the application. 

When an `MLListener` gets instantiated it will first check the `MSAGlobalScriptableObject` to see if a listener prefab has been set. 

- If the `MLListener` prefab has been set, it will instantiate a game object underneath the game object that has either an `AudioListener` or the main camera.

- If the `MLListener` prefab has not been set, it will create a new `MLListener` with default properties.

![MSA Global Scriptable Object](/img/unity/msa_scriptable_object.png)

The `MLListener` prefab allows the developer to configure the desired component properties.


:::note
It is possible to disable the Auto creation feature by unchecking the **Auto Create ML Listener** option.
:::


When an `MLListener` has been automatically created the UI will provide an option to make it a permanent component that could be saved with this scene.

![MLListener Auto Create](/img/unity/ml_listener_auto.png)

This is to ensure that when a developer has manually instantiated an MLPointSource into a scene that didn't have a prior MLListener it can be saved.

## ML Point Source

Enhances Unity's `AudioSource` features by introducing additional parameters such as radiation patterns and offset gain parameters.

![ML Point Source component settings](/img/unity/ml-point-source.png)

**Gain**: Sets the point source gain (in dB).

![ML Point Source component settings](/img/unity/ml-point-source-2.png)

**Distance Properties**: Overrides `AudioSource` distance attenuation calculations.

![ML Point Source component settings](/img/unity/ml-point-source-3.png)

- **Override 3D Properties**: When this option is checked it overrides Unity’s audio source attenuation properties.
- **Min Distance**: Distance at which sound is at full volume.
- **Max Distance**: Distance beyond which sound gets no quieter.
- **Rolloff Factor**:  Modification to real-world distance response.

**Radiation Properties**: Provides radiation properties.

![ML Point Source component settings](/img/unity/ml-point-source-4.png)

- **Billboarding**: This option forces the point source to always align itself to the `MLListener`.
- **Omnidirectional**: This option forces the point source to ignore any directionality completely.
- **Inner Angle**:  Inner cone angle in degrees, within which there is no radiation attenuation.
- **Outer Angle**: Outer cone angle in degrees, beyond which there is full radiation attenuation.
- **Outer Gain**:
  - **Main**: Volume scale beyond outer cone for all freqs.
  - **LF**: Volume scale Beyond outer cone for low freqs.
  - **MF**: Volume scale beyond outer cone for mid freqs.
  - **HF**: Volume scale beyond outer cone for high freqs.

**Obstruction Override**: Overrides default obstruction values.

![ML Point Source component settings](/img/unity/ml-point-source-5.png)

These settings override the direct signal attenuation caused by obstructions between the listener and the source. The values interpolate between the current values set in the `MLListener` Transmission properties and 0dB.

For example if the Main (dB) value in the `MLListener` is set to -13dB then the Main override property will interpolate between -13dB (at 0.0) and 0dB (at 1.0).

**Levels**: Sets the Direct and Indirect levels.

![ML Point Source component settings](/img/unity/ml-point-source-6.png)

- **Direct**: Sets gain and 3-band eq for the direct component of the sound, i.e., the audio mix for the part of the sound not affected by room acoustics.

- **Indirect**: Sets gain and 3-bans eq for the indirect component of the sound, i.e., the audio mix for the part of the sound that's affected by room acoustics (includes reflections and reverb).

- **Indirect Send Levels**:

  - **Dispersion**: Sets gain and 3-band eq for the audio that travels in an indirect way between the source and the listener. For example reflections from objects.

  - **Reverb**: Sets gain and 3-band eq for the reverb component of the sound, i.e., the audio mix for late reverberation caused by room acoustics.

## ML Ambisonic Source

Plays an ambisonic audio clip through an `AudioSource`.

![ML Point Source component settings](/img/unity/ml-ambisonic-source.png)

- **Gain**: Sets the gain of the ambisonic audio source.

**Head Relative**: To get the ambisonic source locked with the listener rotation you need to place the component in the same game object hierarchy and underneath the `MLListener` component.

:::note
For ambisonic sources to work the MSA Ambisonic decoder plugin must be selected in the project settings audio section.
:::

If you need guidance working with ambisonics in Unity (adding ambix files, choosing plugin, etc.), check the [reference docs here](https://docs.unity3d.com/Manual/AmbisonicAudio.html).

## ML Debug Info

This component dictates the amount of debug info that each component will output to the console output in the editor or log output on the device.

![ML Point Source component settings](/img/unity/ml-debug-info.png)

The debug info message has the following format, "**Component Instance ID/Property Name/Value**."

This format makes it easier to identify which component has produced any erroneous values.

### Debug Logging

This component provides different types of logging to output to the Unity console.

:::note
If the `MLDebugInfo` component is not present in the scene then ALL log types will be output by default.
:::

- **Managed Logs**: Displays logs reported by the Unity components (C#)

  - **Managed Log Level**: Selects the type of log messages to display  (Error, Warning, Info)
  - **Enable ML Listener Debug**: Enables logs reported by the ML Listener component
  - **Enable ML Point Source Debug**: Enables logs reported by the ML Point Source component
  - **Enable ML Ambisonic Source Debug**: Enables logs reported by the ML Ambisonic Source component

- **Native Logs**:

  - **Register Native Logs**: Enables logs from the native (C++) plugin

  - **Native Log level**: Selects the type of log messages to display (Error, Warning, Info, Debug, Verbose)

## Unity Analysis Component

:::caution
Even though it doesn't require MLPointSource or `MLListener` in theory, we need to create a valid instance of the plugin library (an internal library) and at this moment, that requires both source and listener in scene, even if not used (we have a bug to work on that). Another important note is that analysis only works on device although we are working in a simulator to be used in editor mode for development/debugging.
:::

When you add the `MLAcousticAnalysis` component, you will see a collection of traits that can be retrieved from the analysis engine. It would look like this:

![Soundfield analysis component](/img/unity/analysis-component.png)

This Editor panel will allow checking the traits of your component. When there is an event with that trait, the last value for that trait will be updated.

There are sets of single values for traits (like level or pitch) and lists of values for other traits (like MFCC for voice, with the list being the values of the different bands).

In the MSA NPM package, there is a very simple example with the Analysis component. It includes a simple script to manipulate the values.

This is the script (where the values are in dB):

```csharp showLineNumbers
using UnityEngine;
using MagicLeap.Soundfield;
using System;
 
public class AnalysisDemo : MonoBehaviour
{
    public GameObject VoiceMeter;
    public GameObject BackgroundMeter;
    private MLAcousticAnalysis myAnalysis;

    void Start()
    {
        myAnalysis = gameObject.GetComponent<MLAcousticAnalysis>();
        Debug.Log("Analysis " + myAnalysis.ToString());
    }
 
    void Update()
    {
        if (myAnalysis)
        {
            // scale voice
            Vector3 scale = VoiceMeter.transform.localScale;
            scale.y = (float)Math.Pow(10.0, myAnalysis.UserVoiceLevelDbfsLastValue / 20.0);
            VoiceMeter.transform.localScale = scale;
            // scale background
            scale = BackgroundMeter.transform.localScale;
            scale.y = (float)Math.Pow(10.0, myAnalysis.AmbientSoundLevelDbfsLastValue / 20.0);
            BackgroundMeter.transform.localScale = scale;
        }
         
    }
}
```

This will change some visual properties of two GameObjects, based on the numerical values polling from the `MLAcousticAnalysis` component, making the scale of the object proportional to the `UserVoiceLevelDbfsLastValue` or `AmbientSoundLevelDbfsLastValue` value.

In editor, this looks like:

![Soundfield analysis component](/img/unity/analysis-component-2.png)

