---
title: ml_hand_tracking.h

---

# ml_hand_tracking.h



## Classes

|                | Name           |
| -------------- | -------------- |
| struct | **[MLHandTrackingCFUIDs](/versioned_docs/version-22-Feb-2023/api-ref/api/Modules/group___hand_tracking/struct_m_l_hand_tracking_c_f_u_i_ds.md)** <br></br>MLCoordinateFrameUIDs for the keypoints.  |
| struct | **[MLHandTrackingStaticData](/versioned_docs/version-22-Feb-2023/api-ref/api/Modules/group___hand_tracking/struct_m_l_hand_tracking_static_data.md)** <br></br>Static information about a hand tracker.  |
| struct | **[MLHandTrackingHandState](/versioned_docs/version-22-Feb-2023/api-ref/api/Modules/group___hand_tracking/struct_m_l_hand_tracking_hand_state.md)** <br></br>State of a single hand.  |
| struct | **[MLHandTrackingData](/versioned_docs/version-22-Feb-2023/api-ref/api/Modules/group___hand_tracking/struct_m_l_hand_tracking_data.md)** <br></br>Data which is received when querying hand tracker from [MLHandTrackingGetData()](/versioned_docs/version-22-Feb-2023/api-ref/api/Modules/group___hand_tracking/group___hand_tracking.md#mlresult-mlhandtrackinggetdata).  |

## Types

|                | Name           |
| -------------- | -------------- |
| typedef struct [MLHandTrackingCFUIDs](/versioned_docs/version-22-Feb-2023/api-ref/api/Modules/group___hand_tracking/struct_m_l_hand_tracking_c_f_u_i_ds.md) | **[MLHandTrackingCFUIDs](/versioned_docs/version-22-Feb-2023/api-ref/api/Modules/group___hand_tracking/group___hand_tracking.md#struct-mlhandtrackingcfuids)** <br></br>MLCoordinateFrameUIDs for the keypoints.  |
| typedef struct [MLHandTrackingStaticData](/versioned_docs/version-22-Feb-2023/api-ref/api/Modules/group___hand_tracking/struct_m_l_hand_tracking_static_data.md) | **[MLHandTrackingStaticData](/versioned_docs/version-22-Feb-2023/api-ref/api/Modules/group___hand_tracking/group___hand_tracking.md#struct-mlhandtrackingstaticdata)** <br></br>Static information about a hand tracker.  |
| typedef struct [MLHandTrackingHandState](/versioned_docs/version-22-Feb-2023/api-ref/api/Modules/group___hand_tracking/struct_m_l_hand_tracking_hand_state.md) | **[MLHandTrackingHandState](/versioned_docs/version-22-Feb-2023/api-ref/api/Modules/group___hand_tracking/group___hand_tracking.md#struct-mlhandtrackinghandstate)** <br></br>State of a single hand.  |
| typedef struct [MLHandTrackingData](/versioned_docs/version-22-Feb-2023/api-ref/api/Modules/group___hand_tracking/struct_m_l_hand_tracking_data.md) | **[MLHandTrackingData](/versioned_docs/version-22-Feb-2023/api-ref/api/Modules/group___hand_tracking/group___hand_tracking.md#struct-mlhandtrackingdata)** <br></br>Data which is received when querying hand tracker from [MLHandTrackingGetData()](/versioned_docs/version-22-Feb-2023/api-ref/api/Modules/group___hand_tracking/group___hand_tracking.md#mlresult-mlhandtrackinggetdata).  |

## Enums

|                | Name           |
| -------------- | -------------- |
| enum | **[MLHandTrackingHandType](/versioned_docs/version-22-Feb-2023/api-ref/api/Modules/group___hand_tracking/group___hand_tracking.md#enums-mlhandtrackinghandtype)** <br></br> { <br></br>[MLHandTrackingHandType_Left](/versioned_docs/version-22-Feb-2023/api-ref/api/Files/ml__hand__tracking_8h.md#enums-mlhandtrackinghandtype-left) = 0,<br></br> [MLHandTrackingHandType_Right](/versioned_docs/version-22-Feb-2023/api-ref/api/Files/ml__hand__tracking_8h.md#enums-mlhandtrackinghandtype-right) = 1,<br></br> [MLHandTrackingHandType_Count](/versioned_docs/version-22-Feb-2023/api-ref/api/Files/ml__hand__tracking_8h.md#enums-mlhandtrackinghandtype-count) = 2,<br></br> [MLHandTrackingHandType_Ensure32Bits](/versioned_docs/version-22-Feb-2023/api-ref/api/Files/ml__hand__tracking_8h.md#enums-mlhandtrackinghandtype-ensure32bits) = 0x7FFFFFFF<br></br>} |
| enum | **[Anonymous Enum 11](/versioned_docs/version-22-Feb-2023/api-ref/api/Modules/group___hand_tracking/group___hand_tracking.md#enums-anonymous-enum-11)** <br></br> { <br></br>[MLHandTrackingStaticData_MaxKeyPoints](/versioned_docs/version-22-Feb-2023/api-ref/api/Files/ml__hand__tracking_8h.md#enums-mlhandtrackingstaticdata-maxkeypoints) = 28<br></br>} |
| enum | **[MLHandTrackingKeyPoint](/versioned_docs/version-22-Feb-2023/api-ref/api/Modules/group___hand_tracking/group___hand_tracking.md#enums-mlhandtrackingkeypoint)** <br></br> { <br></br>[MLHandTrackingKeyPoint_Thumb_Tip](/versioned_docs/version-22-Feb-2023/api-ref/api/Files/ml__hand__tracking_8h.md#enums-mlhandtrackingkeypoint-thumb-tip) = 0,<br></br> [MLHandTrackingKeyPoint_Thumb_IP](/versioned_docs/version-22-Feb-2023/api-ref/api/Files/ml__hand__tracking_8h.md#enums-mlhandtrackingkeypoint-thumb-ip),<br></br> [MLHandTrackingKeyPoint_Thumb_MCP](/versioned_docs/version-22-Feb-2023/api-ref/api/Files/ml__hand__tracking_8h.md#enums-mlhandtrackingkeypoint-thumb-mcp),<br></br> [MLHandTrackingKeyPoint_Thumb_CMC](/versioned_docs/version-22-Feb-2023/api-ref/api/Files/ml__hand__tracking_8h.md#enums-mlhandtrackingkeypoint-thumb-cmc),<br></br> [MLHandTrackingKeyPoint_Index_Tip](/versioned_docs/version-22-Feb-2023/api-ref/api/Files/ml__hand__tracking_8h.md#enums-mlhandtrackingkeypoint-index-tip),<br></br> [MLHandTrackingKeyPoint_Index_DIP](/versioned_docs/version-22-Feb-2023/api-ref/api/Files/ml__hand__tracking_8h.md#enums-mlhandtrackingkeypoint-index-dip),<br></br> [MLHandTrackingKeyPoint_Index_PIP](/versioned_docs/version-22-Feb-2023/api-ref/api/Files/ml__hand__tracking_8h.md#enums-mlhandtrackingkeypoint-index-pip),<br></br> [MLHandTrackingKeyPoint_Index_MCP](/versioned_docs/version-22-Feb-2023/api-ref/api/Files/ml__hand__tracking_8h.md#enums-mlhandtrackingkeypoint-index-mcp),<br></br> [MLHandTrackingKeyPoint_Middle_Tip](/versioned_docs/version-22-Feb-2023/api-ref/api/Files/ml__hand__tracking_8h.md#enums-mlhandtrackingkeypoint-middle-tip),<br></br> [MLHandTrackingKeyPoint_Middle_DIP](/versioned_docs/version-22-Feb-2023/api-ref/api/Files/ml__hand__tracking_8h.md#enums-mlhandtrackingkeypoint-middle-dip),<br></br> [MLHandTrackingKeyPoint_Middle_PIP](/versioned_docs/version-22-Feb-2023/api-ref/api/Files/ml__hand__tracking_8h.md#enums-mlhandtrackingkeypoint-middle-pip),<br></br> [MLHandTrackingKeyPoint_Middle_MCP](/versioned_docs/version-22-Feb-2023/api-ref/api/Files/ml__hand__tracking_8h.md#enums-mlhandtrackingkeypoint-middle-mcp),<br></br> [MLHandTrackingKeyPoint_Ring_Tip](/versioned_docs/version-22-Feb-2023/api-ref/api/Files/ml__hand__tracking_8h.md#enums-mlhandtrackingkeypoint-ring-tip),<br></br> [MLHandTrackingKeyPoint_Ring_DIP](/versioned_docs/version-22-Feb-2023/api-ref/api/Files/ml__hand__tracking_8h.md#enums-mlhandtrackingkeypoint-ring-dip),<br></br> [MLHandTrackingKeyPoint_Ring_PIP](/versioned_docs/version-22-Feb-2023/api-ref/api/Files/ml__hand__tracking_8h.md#enums-mlhandtrackingkeypoint-ring-pip),<br></br> [MLHandTrackingKeyPoint_Ring_MCP](/versioned_docs/version-22-Feb-2023/api-ref/api/Files/ml__hand__tracking_8h.md#enums-mlhandtrackingkeypoint-ring-mcp),<br></br> [MLHandTrackingKeyPoint_Pinky_Tip](/versioned_docs/version-22-Feb-2023/api-ref/api/Files/ml__hand__tracking_8h.md#enums-mlhandtrackingkeypoint-pinky-tip),<br></br> [MLHandTrackingKeyPoint_Pinky_DIP](/versioned_docs/version-22-Feb-2023/api-ref/api/Files/ml__hand__tracking_8h.md#enums-mlhandtrackingkeypoint-pinky-dip),<br></br> [MLHandTrackingKeyPoint_Pinky_PIP](/versioned_docs/version-22-Feb-2023/api-ref/api/Files/ml__hand__tracking_8h.md#enums-mlhandtrackingkeypoint-pinky-pip),<br></br> [MLHandTrackingKeyPoint_Pinky_MCP](/versioned_docs/version-22-Feb-2023/api-ref/api/Files/ml__hand__tracking_8h.md#enums-mlhandtrackingkeypoint-pinky-mcp),<br></br> [MLHandTrackingKeyPoint_Wrist_Center](/versioned_docs/version-22-Feb-2023/api-ref/api/Files/ml__hand__tracking_8h.md#enums-mlhandtrackingkeypoint-wrist-center),<br></br> [MLHandTrackingKeyPoint_Wrist_Ulnar](/versioned_docs/version-22-Feb-2023/api-ref/api/Files/ml__hand__tracking_8h.md#enums-mlhandtrackingkeypoint-wrist-ulnar),<br></br> [MLHandTrackingKeyPoint_Wrist_Radial](/versioned_docs/version-22-Feb-2023/api-ref/api/Files/ml__hand__tracking_8h.md#enums-mlhandtrackingkeypoint-wrist-radial),<br></br> [MLHandTrackingKeyPoint_Hand_Center](/versioned_docs/version-22-Feb-2023/api-ref/api/Files/ml__hand__tracking_8h.md#enums-mlhandtrackingkeypoint-hand-center),<br></br> [MLHandTrackingKeyPoint_Index_Meta](/versioned_docs/version-22-Feb-2023/api-ref/api/Files/ml__hand__tracking_8h.md#enums-mlhandtrackingkeypoint-index-meta),<br></br> [MLHandTrackingKeyPoint_Middle_Meta](/versioned_docs/version-22-Feb-2023/api-ref/api/Files/ml__hand__tracking_8h.md#enums-mlhandtrackingkeypoint-middle-meta),<br></br> [MLHandTrackingKeyPoint_Ring_Meta](/versioned_docs/version-22-Feb-2023/api-ref/api/Files/ml__hand__tracking_8h.md#enums-mlhandtrackingkeypoint-ring-meta),<br></br> [MLHandTrackingKeyPoint_Pinky_Meta](/versioned_docs/version-22-Feb-2023/api-ref/api/Files/ml__hand__tracking_8h.md#enums-mlhandtrackingkeypoint-pinky-meta),<br></br> [MLHandTrackingKeyPoint_Count](/versioned_docs/version-22-Feb-2023/api-ref/api/Files/ml__hand__tracking_8h.md#enums-mlhandtrackingkeypoint-count) = MLHandTrackingStaticData_MaxKeyPoints,<br></br> [MLHandTrackingKeyPoint_Ensure32Bits](/versioned_docs/version-22-Feb-2023/api-ref/api/Files/ml__hand__tracking_8h.md#enums-mlhandtrackingkeypoint-ensure32bits) = 0x7FFFFFFF<br></br>}<br></br>Keypoint index ordering.  |

## Functions

|                | Name           |
| -------------- | -------------- |
| void | **[MLHandTrackingStaticDataInit](/versioned_docs/version-22-Feb-2023/api-ref/api/Modules/group___hand_tracking/group___hand_tracking.md#void-mlhandtrackingstaticdatainit)**([MLHandTrackingStaticData](/versioned_docs/version-22-Feb-2023/api-ref/api/Modules/group___hand_tracking/struct_m_l_hand_tracking_static_data.md) * inout_attr)<br></br>Initializes default values for [MLHandTrackingStaticData](/versioned_docs/version-22-Feb-2023/api-ref/api/Modules/group___hand_tracking/struct_m_l_hand_tracking_static_data.md).  |
| void | **[MLHandTrackingDataInit](/versioned_docs/version-22-Feb-2023/api-ref/api/Modules/group___hand_tracking/group___hand_tracking.md#void-mlhandtrackingdatainit)**([MLHandTrackingData](/versioned_docs/version-22-Feb-2023/api-ref/api/Modules/group___hand_tracking/struct_m_l_hand_tracking_data.md) * inout_attr)<br></br>Initializes values for [MLHandTrackingData](/versioned_docs/version-22-Feb-2023/api-ref/api/Modules/group___hand_tracking/struct_m_l_hand_tracking_data.md).  |
| [MLResult](/versioned_docs/version-22-Feb-2023/api-ref/api/Modules/group___platform/group___platform.md#int32-t-mlresult) | **[MLHandTrackingCreate](/versioned_docs/version-22-Feb-2023/api-ref/api/Modules/group___hand_tracking/group___hand_tracking.md#mlresult-mlhandtrackingcreate)**([MLHandle](/versioned_docs/version-22-Feb-2023/api-ref/api/Modules/group___platform/group___platform.md#uint64-t-mlhandle) * out_handle)<br></br>Creates a hand tracker.  |
| [MLResult](/versioned_docs/version-22-Feb-2023/api-ref/api/Modules/group___platform/group___platform.md#int32-t-mlresult) | **[MLHandTrackingDestroy](/versioned_docs/version-22-Feb-2023/api-ref/api/Modules/group___hand_tracking/group___hand_tracking.md#mlresult-mlhandtrackingdestroy)**([MLHandle](/versioned_docs/version-22-Feb-2023/api-ref/api/Modules/group___platform/group___platform.md#uint64-t-mlhandle) hand_tracker)<br></br>Destroys a hand tracker.  |
| [MLResult](/versioned_docs/version-22-Feb-2023/api-ref/api/Modules/group___platform/group___platform.md#int32-t-mlresult) | **[MLHandTrackingGetData](/versioned_docs/version-22-Feb-2023/api-ref/api/Modules/group___hand_tracking/group___hand_tracking.md#mlresult-mlhandtrackinggetdata)**([MLHandle](/versioned_docs/version-22-Feb-2023/api-ref/api/Modules/group___platform/group___platform.md#uint64-t-mlhandle) hand_tracker, [MLHandTrackingData](/versioned_docs/version-22-Feb-2023/api-ref/api/Modules/group___hand_tracking/struct_m_l_hand_tracking_data.md) * out_data)<br></br>Queries the state of the hand tracker.  |
| [MLResult](/versioned_docs/version-22-Feb-2023/api-ref/api/Modules/group___platform/group___platform.md#int32-t-mlresult) | **[MLHandTrackingGetStaticData](/versioned_docs/version-22-Feb-2023/api-ref/api/Modules/group___hand_tracking/group___hand_tracking.md#mlresult-mlhandtrackinggetstaticdata)**([MLHandle](/versioned_docs/version-22-Feb-2023/api-ref/api/Modules/group___platform/group___platform.md#uint64-t-mlhandle) hand_tracker, [MLHandTrackingStaticData](/versioned_docs/version-22-Feb-2023/api-ref/api/Modules/group___hand_tracking/struct_m_l_hand_tracking_static_data.md) * out_data)<br></br>Gets static information about hand tracking system.  |

## Enums Documentation

### MLHandTrackingHandType {#enums-mlhandtrackinghandtype}

| Enumerator | Value | Description |
| ---------- | ----- | ----------- |
| MLHandTrackingHandType_Left |  0| Left hand. |
| MLHandTrackingHandType_Right |  1| Right hand. |
| MLHandTrackingHandType_Count |  2| Number of hands. |
| MLHandTrackingHandType_Ensure32Bits |  0x7FFFFFFF| Ensure enum is represented as 32 bits. |




Available hand types. 





-----------

### Anonymous Enum 11 {#enums-anonymous-enum-11}

| Enumerator | Value | Description |
| ---------- | ----- | ----------- |
| MLHandTrackingStaticData_MaxKeyPoints |  28| Maximum number of key points per hand. |








-----------

### MLHandTrackingKeyPoint {#enums-mlhandtrackingkeypoint}

| Enumerator | Value | Description |
| ---------- | ----- | ----------- |
| MLHandTrackingKeyPoint_Thumb_Tip |  0| |
| MLHandTrackingKeyPoint_Thumb_IP | | |
| MLHandTrackingKeyPoint_Thumb_MCP | | |
| MLHandTrackingKeyPoint_Thumb_CMC | | |
| MLHandTrackingKeyPoint_Index_Tip | | |
| MLHandTrackingKeyPoint_Index_DIP | | |
| MLHandTrackingKeyPoint_Index_PIP | | |
| MLHandTrackingKeyPoint_Index_MCP | | |
| MLHandTrackingKeyPoint_Middle_Tip | | |
| MLHandTrackingKeyPoint_Middle_DIP | | |
| MLHandTrackingKeyPoint_Middle_PIP | | |
| MLHandTrackingKeyPoint_Middle_MCP | | |
| MLHandTrackingKeyPoint_Ring_Tip | | |
| MLHandTrackingKeyPoint_Ring_DIP | | |
| MLHandTrackingKeyPoint_Ring_PIP | | |
| MLHandTrackingKeyPoint_Ring_MCP | | |
| MLHandTrackingKeyPoint_Pinky_Tip | | |
| MLHandTrackingKeyPoint_Pinky_DIP | | |
| MLHandTrackingKeyPoint_Pinky_PIP | | |
| MLHandTrackingKeyPoint_Pinky_MCP | | |
| MLHandTrackingKeyPoint_Wrist_Center | | |
| MLHandTrackingKeyPoint_Wrist_Ulnar | | |
| MLHandTrackingKeyPoint_Wrist_Radial | | |
| MLHandTrackingKeyPoint_Hand_Center | | |
| MLHandTrackingKeyPoint_Index_Meta | | |
| MLHandTrackingKeyPoint_Middle_Meta | | |
| MLHandTrackingKeyPoint_Ring_Meta | | |
| MLHandTrackingKeyPoint_Pinky_Meta | | |
| MLHandTrackingKeyPoint_Count |  MLHandTrackingStaticData_MaxKeyPoints| Maximum number of key points per gesture. |
| MLHandTrackingKeyPoint_Ensure32Bits |  0x7FFFFFFF| |



Keypoint index ordering. 

The index ordering of 28 keypoints exposed in array keypoints_mask[MLHandTrackingStaticData_MaxKeyPoints] and left_frame/right_frame[MLHandTrackingStaticData_MaxKeyPoints].




**API Level:**
  * 7 




-----------


## Types Documentation

### MLHandTrackingCFUIDs {#struct-mlhandtrackingcfuids}

```cpp
typedef struct MLHandTrackingCFUIDs  MLHandTrackingCFUIDs;
```

MLCoordinateFrameUIDs for the keypoints. 

See [MLHandTrackingKeyPoint](/versioned_docs/version-22-Feb-2023/api-ref/api/Modules/group___hand_tracking/group___hand_tracking.md#enum-mlhandtrackingkeypoint) for more details.



[More Info](/versioned_docs/version-22-Feb-2023/api-ref/api/Modules/group___hand_tracking/struct_m_l_hand_tracking_c_f_u_i_ds.md)


**API Level:**
  * 20 




-----------

### MLHandTrackingStaticData {#struct-mlhandtrackingstaticdata}

```cpp
typedef struct MLHandTrackingStaticData  MLHandTrackingStaticData;
```

Static information about a hand tracker. 

This structure must be initialized by calling [MLHandTrackingStaticDataInit()](/versioned_docs/version-22-Feb-2023/api-ref/api/Modules/group___hand_tracking/group___hand_tracking.md#void-mlhandtrackingstaticdatainit) before use.



[More Info](/versioned_docs/version-22-Feb-2023/api-ref/api/Modules/group___hand_tracking/struct_m_l_hand_tracking_static_data.md)


**API Level:**
  * 20 




-----------

### MLHandTrackingHandState {#struct-mlhandtrackinghandstate}

```cpp
typedef struct MLHandTrackingHandState  MLHandTrackingHandState;
```

State of a single hand. 



[More Info](/versioned_docs/version-22-Feb-2023/api-ref/api/Modules/group___hand_tracking/struct_m_l_hand_tracking_hand_state.md)


**API Level:**
  * 20 




-----------

### MLHandTrackingData {#struct-mlhandtrackingdata}

```cpp
typedef struct MLHandTrackingData  MLHandTrackingData;
```

Data which is received when querying hand tracker from [MLHandTrackingGetData()](/versioned_docs/version-22-Feb-2023/api-ref/api/Modules/group___hand_tracking/group___hand_tracking.md#mlresult-mlhandtrackinggetdata). 

This structure must be initialized by calling [MLHandTrackingDataInit()](/versioned_docs/version-22-Feb-2023/api-ref/api/Modules/group___hand_tracking/group___hand_tracking.md#void-mlhandtrackingdatainit) before use.



[More Info](/versioned_docs/version-22-Feb-2023/api-ref/api/Modules/group___hand_tracking/struct_m_l_hand_tracking_data.md)


**API Level:**
  * 20 




-----------


## Functions Documentation

### MLHandTrackingStaticDataInit {#void-mlhandtrackingstaticdatainit}

```cpp
static inline void MLHandTrackingStaticDataInit(
    MLHandTrackingStaticData * inout_attr
)
```

Initializes default values for [MLHandTrackingStaticData](/versioned_docs/version-22-Feb-2023/api-ref/api/Modules/group___hand_tracking/struct_m_l_hand_tracking_static_data.md). 

**Parameters**

|  |   |   |
|--|--|--|
| [MLHandTrackingStaticData](/versioned_docs/version-22-Feb-2023/api-ref/api/Modules/group___hand_tracking/struct_m_l_hand_tracking_static_data.md) * |inout_attr|The object to initialize with default values. |



**API Level:**
  * 20




-----------

### MLHandTrackingDataInit {#void-mlhandtrackingdatainit}

```cpp
static inline void MLHandTrackingDataInit(
    MLHandTrackingData * inout_attr
)
```

Initializes values for [MLHandTrackingData](/versioned_docs/version-22-Feb-2023/api-ref/api/Modules/group___hand_tracking/struct_m_l_hand_tracking_data.md). 

**Parameters**

|  |   |   |
|--|--|--|
| [MLHandTrackingData](/versioned_docs/version-22-Feb-2023/api-ref/api/Modules/group___hand_tracking/struct_m_l_hand_tracking_data.md) * |inout_attr|The object to initialize. |



**API Level:**
  * 20




-----------

### MLHandTrackingCreate {#mlresult-mlhandtrackingcreate}

```cpp
MLResult MLHandTrackingCreate(
    MLHandle * out_handle
)
```

Creates a hand tracker. 

**Parameters**

|  |   |   |
|--|--|--|
| [MLHandle](/versioned_docs/version-22-Feb-2023/api-ref/api/Modules/group___platform/group___platform.md#uint64-t-mlhandle) * |out_handle|A pointer to an [MLHandle](/versioned_docs/version-22-Feb-2023/api-ref/api/Modules/group___platform/group___platform.md#uint64-t-mlhandle) which will contain the handle of the hand tracker. If this operation fails, out_handle will be [ML_INVALID_HANDLE](/versioned_docs/version-22-Feb-2023/api-ref/api/Modules/group___platform/group___platform.md#enums-ml-invalid-handle).|

**Returns**

|  |   |   |
|--|--|--|
| [MLResult](/versioned_docs/version-22-Feb-2023/api-ref/api/Modules/group___platform/group___platform.md#int32-t-mlresult) |MLResult_InvalidParam|out_handle is null. |
| [MLResult](/versioned_docs/version-22-Feb-2023/api-ref/api/Modules/group___platform/group___platform.md#int32-t-mlresult) |MLResult_Ok|The tracker was created successfully. |
| [MLResult](/versioned_docs/version-22-Feb-2023/api-ref/api/Modules/group___platform/group___platform.md#int32-t-mlresult) |MLResult_PermissionDenied|The application lacks permission. |
| [MLResult](/versioned_docs/version-22-Feb-2023/api-ref/api/Modules/group___platform/group___platform.md#int32-t-mlresult) |MLResult_UnspecifiedFailure|It failed to create the tracker.|
**Required Permissions**:

  * com.magicleap.permission.HAND_TRACKING (protection level: normal) 






-----------

### MLHandTrackingDestroy {#mlresult-mlhandtrackingdestroy}

```cpp
MLResult MLHandTrackingDestroy(
    MLHandle hand_tracker
)
```

Destroys a hand tracker. 

**Parameters**

|  |   |   |
|--|--|--|
| [MLHandle](/versioned_docs/version-22-Feb-2023/api-ref/api/Modules/group___platform/group___platform.md#uint64-t-mlhandle) |hand_tracker|A handle to a Hand Tracker created by [MLHandTrackingCreate()](/versioned_docs/version-22-Feb-2023/api-ref/api/Modules/group___hand_tracking/group___hand_tracking.md#mlresult-mlhandtrackingcreate).|

**Returns**

|  |   |   |
|--|--|--|
| [MLResult](/versioned_docs/version-22-Feb-2023/api-ref/api/Modules/group___platform/group___platform.md#int32-t-mlresult) |MLResult_Ok|It successfully destroyed the tracker. |
| [MLResult](/versioned_docs/version-22-Feb-2023/api-ref/api/Modules/group___platform/group___platform.md#int32-t-mlresult) |MLResult_UnspecifiedFailure|It failed to destroy the tracker.|
**Required Permissions**:

  * None 






-----------

### MLHandTrackingGetData {#mlresult-mlhandtrackinggetdata}

```cpp
MLResult MLHandTrackingGetData(
    MLHandle hand_tracker,
    MLHandTrackingData * out_data
)
```

Queries the state of the hand tracker. 

**Parameters**

|  |   |   |
|--|--|--|
| [MLHandle](/versioned_docs/version-22-Feb-2023/api-ref/api/Modules/group___platform/group___platform.md#uint64-t-mlhandle) |hand_tracker|A handle to a Hand Tracker created by [MLHandTrackingCreate()](/versioned_docs/version-22-Feb-2023/api-ref/api/Modules/group___hand_tracking/group___hand_tracking.md#mlresult-mlhandtrackingcreate). |
| [MLHandTrackingData](/versioned_docs/version-22-Feb-2023/api-ref/api/Modules/group___hand_tracking/struct_m_l_hand_tracking_data.md) * |out_data|Pointer to a variable that receives information about the tracked hands.|

**Returns**

|  |   |   |
|--|--|--|
| [MLResult](/versioned_docs/version-22-Feb-2023/api-ref/api/Modules/group___platform/group___platform.md#int32-t-mlresult) |MLResult_InvalidParam|out_data is null or out_data->version is not set. |
| [MLResult](/versioned_docs/version-22-Feb-2023/api-ref/api/Modules/group___platform/group___platform.md#int32-t-mlresult) |MLResult_Ok|The hand information was available and the information in out_data is valid. |
| [MLResult](/versioned_docs/version-22-Feb-2023/api-ref/api/Modules/group___platform/group___platform.md#int32-t-mlresult) |MLResult_UnspecifiedFailure|It failed to get the hand information.|
**Required Permissions**:

  * None 





**API Level:**
  * 20




-----------

### MLHandTrackingGetStaticData {#mlresult-mlhandtrackinggetstaticdata}

```cpp
MLResult MLHandTrackingGetStaticData(
    MLHandle hand_tracker,
    MLHandTrackingStaticData * out_data
)
```

Gets static information about hand tracking system. 

**Parameters**

|  |   |   |
|--|--|--|
| [MLHandle](/versioned_docs/version-22-Feb-2023/api-ref/api/Modules/group___platform/group___platform.md#uint64-t-mlhandle) |hand_tracker|A handle to a Hand Tracker created by [MLHandTrackingCreate()](/versioned_docs/version-22-Feb-2023/api-ref/api/Modules/group___hand_tracking/group___hand_tracking.md#mlresult-mlhandtrackingcreate). |
| [MLHandTrackingStaticData](/versioned_docs/version-22-Feb-2023/api-ref/api/Modules/group___hand_tracking/struct_m_l_hand_tracking_static_data.md) * |out_data|Pointer to a variable that receives static data about the hand tracker.|

**Returns**

|  |   |   |
|--|--|--|
| [MLResult](/versioned_docs/version-22-Feb-2023/api-ref/api/Modules/group___platform/group___platform.md#int32-t-mlresult) |MLResult_InvalidParam|out_data is null or out_data->version is not set. |
| [MLResult](/versioned_docs/version-22-Feb-2023/api-ref/api/Modules/group___platform/group___platform.md#int32-t-mlresult) |MLResult_Ok|The hand information was available and the information in out_data is valid. |
| [MLResult](/versioned_docs/version-22-Feb-2023/api-ref/api/Modules/group___platform/group___platform.md#int32-t-mlresult) |MLResult_UnspecifiedFailure|It failed to get the hand information.|
**Required Permissions**:

  * None 


See [MLHandTrackingStaticData](/versioned_docs/version-22-Feb-2023/api-ref/api/Modules/group___hand_tracking/struct_m_l_hand_tracking_static_data.md) for more details. .




**API Level:**
  * 20




-----------



## Source code

```cpp
// %BANNER_BEGIN%
// ---------------------------------------------------------------------
// %COPYRIGHT_BEGIN%
// Copyright (c) 2017 Magic Leap, Inc. All Rights Reserved.
// Use of this file is governed by the Software License Agreement,
// located here: https://www.magicleap.com/software-license-agreement-ml2
// Terms and conditions applicable to third-party materials accompanying
// this distribution may also be found in the top-level NOTICE file
// appearing herein.
// %COPYRIGHT_END%
// ---------------------------------------------------------------------
// %BANNER_END%

#pragma once

#include "ml_api.h"
#include "ml_types.h"

#include <string.h>

ML_EXTERN_C_BEGIN

typedef enum MLHandTrackingHandType {
  MLHandTrackingHandType_Left = 0,
  MLHandTrackingHandType_Right = 1,
  MLHandTrackingHandType_Count = 2,
  MLHandTrackingHandType_Ensure32Bits = 0x7FFFFFFF
} MLHandTrackingHandType;

enum {
  MLHandTrackingStaticData_MaxKeyPoints = 28
};

typedef enum MLHandTrackingKeyPoint {
  MLHandTrackingKeyPoint_Thumb_Tip = 0,
  MLHandTrackingKeyPoint_Thumb_IP,
  MLHandTrackingKeyPoint_Thumb_MCP,
  MLHandTrackingKeyPoint_Thumb_CMC,
  MLHandTrackingKeyPoint_Index_Tip,
  MLHandTrackingKeyPoint_Index_DIP,
  MLHandTrackingKeyPoint_Index_PIP,
  MLHandTrackingKeyPoint_Index_MCP,
  MLHandTrackingKeyPoint_Middle_Tip,
  MLHandTrackingKeyPoint_Middle_DIP,
  MLHandTrackingKeyPoint_Middle_PIP,
  MLHandTrackingKeyPoint_Middle_MCP,
  MLHandTrackingKeyPoint_Ring_Tip,
  MLHandTrackingKeyPoint_Ring_DIP,
  MLHandTrackingKeyPoint_Ring_PIP,
  MLHandTrackingKeyPoint_Ring_MCP,
  MLHandTrackingKeyPoint_Pinky_Tip,
  MLHandTrackingKeyPoint_Pinky_DIP,
  MLHandTrackingKeyPoint_Pinky_PIP,
  MLHandTrackingKeyPoint_Pinky_MCP,
  MLHandTrackingKeyPoint_Wrist_Center,
  MLHandTrackingKeyPoint_Wrist_Ulnar,
  MLHandTrackingKeyPoint_Wrist_Radial,
  MLHandTrackingKeyPoint_Hand_Center,
  MLHandTrackingKeyPoint_Index_Meta,
  MLHandTrackingKeyPoint_Middle_Meta,
  MLHandTrackingKeyPoint_Ring_Meta,
  MLHandTrackingKeyPoint_Pinky_Meta,
  MLHandTrackingKeyPoint_Count = MLHandTrackingStaticData_MaxKeyPoints,
  MLHandTrackingKeyPoint_Ensure32Bits = 0x7FFFFFFF
} MLHandTrackingKeyPoint;


typedef struct MLHandTrackingCFUIDs {
  MLCoordinateFrameUID keypoint_cfuids[MLHandTrackingStaticData_MaxKeyPoints];
} MLHandTrackingCFUIDs;

typedef struct MLHandTrackingStaticData {
  uint32_t version;
  MLHandTrackingCFUIDs hand_cfuids[MLHandTrackingHandType_Count];
} MLHandTrackingStaticData;

ML_STATIC_INLINE void MLHandTrackingStaticDataInit(MLHandTrackingStaticData *inout_attr) {
  if (NULL != inout_attr) {
    memset(inout_attr, 0, sizeof(MLHandTrackingStaticData));
    inout_attr->version = 2u;
  }
}

typedef struct MLHandTrackingHandState {
  bool is_hand_detected;
  float hand_confidence;
  bool keypoints_mask[MLHandTrackingStaticData_MaxKeyPoints];
} MLHandTrackingHandState;

typedef struct MLHandTrackingData {
  uint32_t version;

  MLHandTrackingHandState hand_state[MLHandTrackingHandType_Count];

  MLTime timestamp_ns;

} MLHandTrackingData;

ML_STATIC_INLINE void MLHandTrackingDataInit(MLHandTrackingData *inout_attr) {
  if (NULL != inout_attr) {
    memset(inout_attr, 0, sizeof(MLHandTrackingData));
    inout_attr->version = 3u;
  }
}

ML_API MLResult ML_CALL MLHandTrackingCreate(MLHandle *out_handle);

ML_API MLResult ML_CALL MLHandTrackingDestroy(MLHandle hand_tracker);

ML_API MLResult ML_CALL MLHandTrackingGetData(MLHandle hand_tracker, MLHandTrackingData *out_data);

ML_API MLResult ML_CALL MLHandTrackingGetStaticData(MLHandle hand_tracker, MLHandTrackingStaticData *out_data);

ML_EXTERN_C_END
```




