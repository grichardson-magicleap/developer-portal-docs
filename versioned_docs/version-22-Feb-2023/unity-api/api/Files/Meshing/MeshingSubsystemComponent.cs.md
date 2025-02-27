---

title: MeshingSubsystemComponent.cs

---


# MeshingSubsystemComponent.cs









## Source code

```csharp
// %BANNER_BEGIN%
// ---------------------------------------------------------------------
// %COPYRIGHT_BEGIN%
// Copyright (c) (2021-2022) Magic Leap, Inc. All Rights Reserved.
// Use of this file is governed by the Software License Agreement, located here: https://www.magicleap.com/software-license-agreement-ml2
// Terms and conditions applicable to third-party materials accompanying this distribution may also be found in the top-level NOTICE file appearing herein.
// %COPYRIGHT_END%
// ---------------------------------------------------------------------
// %BANNER_END%

using System;
using System.Collections;
using System.Collections.Generic;
using System.Diagnostics;
using System.Runtime.InteropServices;
using UnityEngine.Serialization;
using UnityEngine.XR.ARSubsystems;
using UnityEngine.XR.Management;

#if UNITY_EDITOR
using UnityEditor;
//using UnityEditor.XR.MagicLeap.Remote;
#endif

namespace UnityEngine.XR.MagicLeap
{
    [DisallowMultipleComponent]
    public sealed class MeshingSubsystemComponent : MonoBehaviour
    {
        public enum MeshType
        {
            Triangles,

            PointCloud
        }

        [Obsolete("This enum will be removed in a future release. Instead, use MeshingSubsystem.Extensions.MLMeshing.LevelOfDetail.")]
        public enum LevelOfDetail
        {
            Minimum,

            Medium,

            Maximum
        }

        [SerializeField]
        GameObject m_MeshPrefab;

        public GameObject meshPrefab
        {
            get { return m_MeshPrefab; }
            set { m_MeshPrefab = value; }
        }

        public void OnMeshingPropertyChanged() => m_SettingsDirty = true;

        [SerializeField]
        [OnChangedCall(nameof(OnMeshingPropertyChanged))]
        bool m_ComputeNormals = true;

        public bool computeNormals
        {
            get { return m_ComputeNormals; }
            set
            {
                if (m_ComputeNormals != value)
                {
                    m_ComputeNormals = value;
                    m_SettingsDirty = true;
                }
            }
        }

        public static MeshingSubsystem.Extensions.MLMeshing.LevelOfDetail FromDensityToLevelOfDetail(float density)
        {
            if (density < 0.33f)
                return MeshingSubsystem.Extensions.MLMeshing.LevelOfDetail.Minimum;
            else if (density < 0.66f)
                return MeshingSubsystem.Extensions.MLMeshing.LevelOfDetail.Medium;
            else
                return MeshingSubsystem.Extensions.MLMeshing.LevelOfDetail.Maximum;
        }

        public static float FromLevelOfDetailToDensity(MeshingSubsystem.Extensions.MLMeshing.LevelOfDetail lod)
        {
            if (lod == MeshingSubsystem.Extensions.MLMeshing.LevelOfDetail.Minimum)
                return 0.0f;
            else if (lod == MeshingSubsystem.Extensions.MLMeshing.LevelOfDetail.Medium)
                return 0.5f;
            else
                return 1.0f;
        }

        [Obsolete("This function will be removed in a future release. Instead, use FromLevelOfDetailToDensity().")]
        public static float LevelOfDetailToDensity(LevelOfDetail lod)
        {
            if (lod == LevelOfDetail.Minimum)
                return 0.0f;
            else if (lod == LevelOfDetail.Medium)
                return 0.5f;
            else
                return 1.0f;
        }

        [Obsolete("This function will be removed in a future release. Instead, use FromDensityToLevelOfDetail().")]
        public static LevelOfDetail DensityToLevelOfDetail(float density)
        {
            if (density < 0.33f)
                return LevelOfDetail.Minimum;
            else if (density < 0.66f)
                return LevelOfDetail.Medium;
            else
                return LevelOfDetail.Maximum;
        }

        [SerializeField, Tooltip("Determines the level of detail that the batched mesh blocks should be. This property is not used if custom mesh block requests are created via the SetCustomMeshBlockRequests() method.")]
        [OnChangedCall(nameof(OnMeshingPropertyChanged))]
        float m_Density = 1.0f;

        public float density
        {
            get { return m_Density; }
            set
            {
                if (m_Density != value)
                {
                    m_Density = value;
                    m_SettingsDirty = true;
                }
            }
        }

        [SerializeField,Tooltip("Determines how many mesh blocks should be requested by the meshing subsystem at once. This property is not used if custom mesh block requests are created via the SetCustomMeshBlockRequests() method.")]
        [OnChangedCall(nameof(OnMeshingPropertyChanged))]
        int m_BatchSize = 16;

        public int batchSize
        {
            get { return m_BatchSize; }
            set
            {
                if (m_BatchSize != value)
                {
                    m_BatchSize = value;
                    m_SettingsDirty = true;
                }
            }
        }

        [SerializeField]
        Transform m_MeshParent;

        public Transform meshParent
        {
            get { return m_MeshParent; }
            set { m_MeshParent = value; }
        }

        [SerializeField]
        [FormerlySerializedAs("m_MeshType")]
        [OnChangedCall(nameof(OnMeshingPropertyChanged))]
        MeshType m_RequestedMeshType = MeshType.Triangles;

        public MeshType currentMeshType => SubsystemFeatures.currentFeatures.HasFlag(Feature.Meshing) ? MeshType.Triangles : MeshType.PointCloud;

        public MeshType requestedMeshType
        {
            get { return m_RequestedMeshType; }
            set
            {
                if (m_RequestedMeshType != value)
                {
                    m_RequestedMeshType = value;
                    m_SettingsDirty = true;
                }
            }
        }

        [SerializeField]
        [OnChangedCall(nameof(OnMeshingPropertyChanged))]
        float m_FillHoleLength = 1.0f;

        public float fillHoleLength
        {
            get { return m_FillHoleLength; }
            set
            {
                if (m_FillHoleLength != value)
                {
                    m_FillHoleLength = value;
                    m_SettingsDirty = true;
                }
            }
        }

        [SerializeField]
        [OnChangedCall(nameof(OnMeshingPropertyChanged))]
        bool m_Planarize = false;

        public bool planarize
        {
            get { return m_Planarize; }
            set
            {
                if (m_Planarize != value)
                {
                    m_Planarize = value;
                    m_SettingsDirty = true;
                }
            }
        }

        [SerializeField]
        [OnChangedCall(nameof(OnMeshingPropertyChanged))]
        float m_DisconnectedComponentArea = 0.25f;

        public float disconnectedComponentArea
        {
            get { return m_DisconnectedComponentArea; }
            set
            {
                if (m_DisconnectedComponentArea != value)
                {
                    m_DisconnectedComponentArea = value;
                    m_SettingsDirty = true;
                }
            }
        }

        [SerializeField]
        uint m_MeshQueueSize = 4;

        public uint meshQueueSize
        {
            get { return m_MeshQueueSize; }
            set { m_MeshQueueSize = value; }
        }

        [SerializeField]
        float m_PollingRate = 0.25f;

        public float pollingRate
        {
            get { return m_PollingRate; }
            set { m_PollingRate = value; }
        }

        [SerializeField]
        [OnChangedCall(nameof(OnMeshingPropertyChanged))]
        bool m_RequestVertexConfidence = false;

        public bool requestVertexConfidence
        {
            get { return m_RequestVertexConfidence; }
            set
            {
                if (m_RequestVertexConfidence != value)
                {
                    m_RequestVertexConfidence = value;
                    m_SettingsDirty = true;
                }
            }
        }

        [SerializeField]
        [OnChangedCall(nameof(OnMeshingPropertyChanged))]
        bool m_RemoveMeshSkirt = false;

        public bool removeMeshSkirt
        {
            get { return m_RemoveMeshSkirt; }
            set
            {
                if (m_RemoveMeshSkirt != value)
                {
                    m_RemoveMeshSkirt = value;
                    m_SettingsDirty = true;
                }
            }
        }

        Vector3 boundsExtents
        {
            get { return transform.localScale; }
        }

        public Dictionary<MeshId, GameObject> meshIdToGameObjectMap { get; private set; }

        public event Action<MeshId> meshAdded;

        public event Action<MeshId> meshUpdated;

        public event Action<MeshId> meshRemoved;

        private InputDevice headDevice;

        public bool TryGetConfidence(MeshId meshId, List<float> confidenceOut)
        {
            if (confidenceOut == null)
            {
                throw new ArgumentNullException("confidenceOut");
            }

            if (m_MeshSubsystem == null)
            {
                return false;
            }

            int count = 0;
            var floatPtr = MeshingSubsystem.Extensions.MLMeshing.Config.AcquireConfidence(meshId, out count);
            if (floatPtr == IntPtr.Zero)
            {
                return false;
            }

            confidenceOut.Clear();
            if (count > 0)
            {
                Span<float> floatSpan;
                unsafe
                {
                    floatSpan = new Span<float>(floatPtr.ToPointer(), count);
                }

                for (int i = 0; i < count; ++i)
                {
                    confidenceOut.Add(floatSpan[i]);
                }
            }
            MeshingSubsystem.Extensions.MLMeshing.Config.ReleaseConfidence(meshId);
            return true;
        }

        public void DestroyAllMeshes()
        {
            foreach (var kvp in meshIdToGameObjectMap)
            {
                var mesh = kvp.Value;
                Destroy(mesh);
            }

            meshIdToGameObjectMap.Clear();
            m_MeshesBeingGenerated.Clear();
            m_MeshesNeedingGeneration.Clear();
        }

        public void RefreshMesh(MeshId meshId)
        {
            if (m_MeshesBeingGenerated.ContainsKey(meshId))
            {
                return;
            }

            m_MeshesNeedingGeneration[meshId] = new MeshInfo
            {
                MeshId = meshId,
                ChangeState = MeshChangeState.Updated,
                PriorityHint = Time.frameCount
            };
        }

        public void RefreshAllMeshes()
        {
            foreach (var kvp in meshIdToGameObjectMap)
            {
                var meshId = kvp.Key;
                RefreshMesh(meshId);
            }
        }

        public static void SetCustomMeshBlockRequests(MeshingSubsystem.Extensions.MLMeshing.OnMeshBlockRequests onBlockRequests) => MeshingSubsystem.Extensions.MLMeshing.Config.SetCustomMeshBlockRequests(onBlockRequests);

#if UNITY_EDITOR
        MeshingSubsystem.Extensions.MLMeshing.Config.Settings m_CachedSettings;
        float m_CachedDensity;

        bool haveSettingsChanged
        {
            get
            {
                var currentSettings = GetMeshingSettings();
                return
                    (m_CachedDensity != density) ||
                    (m_CachedSettings.fillHoleLength != currentSettings.fillHoleLength) ||
                    (m_CachedSettings.flags != currentSettings.flags) ||
                    (m_CachedSettings.disconnectedComponentArea != currentSettings.disconnectedComponentArea);
            }
        }
#endif

        MeshingSubsystem.Extensions.MLMeshing.Config.Settings GetMeshingSettings()
        {
            var flags = MeshingSubsystem.Extensions.MLMeshing.Config.Flags.IndexOrderCW;

            if (computeNormals)
                flags |= MeshingSubsystem.Extensions.MLMeshing.Config.Flags.ComputeNormals;
            if (requestVertexConfidence)
                flags |= MeshingSubsystem.Extensions.MLMeshing.Config.Flags.ComputeConfidence;
            if (planarize)
                flags |= MeshingSubsystem.Extensions.MLMeshing.Config.Flags.Planarize;
            if (removeMeshSkirt)
                flags |= MeshingSubsystem.Extensions.MLMeshing.Config.Flags.RemoveMeshSkirt;
            if (requestedMeshType == MeshType.PointCloud)
                flags |= MeshingSubsystem.Extensions.MLMeshing.Config.Flags.PointCloud;
            var settings = new MeshingSubsystem.Extensions.MLMeshing.Config.Settings
            {
                flags = flags,
                fillHoleLength = fillHoleLength,
                disconnectedComponentArea = disconnectedComponentArea
            };

            return settings;
        }

        void OnDrawGizmosSelected()
        {
            Gizmos.color = new Color(0, .5f, 0, .35f);
            Gizmos.matrix = transform.localToWorldMatrix;
            Gizmos.DrawCube(Vector3.zero, Vector3.one);
        }

        // Create new GameObject and parent to ourself
        GameObject CreateGameObject(MeshId meshId)
        {
            GameObject newGameObject = Instantiate(m_MeshPrefab, meshParent);
            newGameObject.name = string.Format("Mesh {0}", meshId);
            newGameObject.SetActive(true);
            return newGameObject;
        }

        GameObject GetOrCreateGameObject(MeshId meshId)
        {
            GameObject go = null;
            if (!meshIdToGameObjectMap.TryGetValue(meshId, out go))
            {
                go = CreateGameObject(meshId);
                meshIdToGameObjectMap[meshId] = go;
            }

            return go;
        }

        void Awake()
        {
            meshIdToGameObjectMap = new Dictionary<MeshId, GameObject>();
            m_MeshesNeedingGeneration = new Dictionary<MeshId, MeshInfo>();
            m_MeshesBeingGenerated = new Dictionary<MeshId, MeshInfo>();
        }


        IEnumerator Init()
        {
            while (XRGeneralSettings.Instance == null)
            {
                yield return null;
            }
            while (XRGeneralSettings.Instance.Manager == null)
            {
                yield return null;
            }
            m_Loader = XRGeneralSettings.Instance.Manager.ActiveLoaderAs<MagicLeapLoader>();
            if (m_Loader != null)
            {
                m_MeshSubsystem = m_Loader.meshSubsystem;
            }

            UpdateSettings();
            UpdateBounds();
            UpdateBatchSize();

            StartSubsystem();
        }

        void StartSubsystem()
        {
            if (m_Loader != null)
            {
                m_Loader.StartMeshSubsystem();
            }
        }

        void StopSubsystem()
        {
            if (m_Loader != null)
            {
                m_Loader.StopMeshSubsystem();
            }
            m_MeshSubsystem = null;
            SubsystemFeatures.SetCurrentFeatureEnabled(Feature.Meshing | Feature.PointCloud, false);
        }

        void OnEnable()
        {
            StartCoroutine(Init());
        }

        void OnDisable()
        {
            StopSubsystem();
        }

        void AddToQueueIfNecessary(MeshInfo meshInfo)
        {
            if (m_MeshesNeedingGeneration.ContainsKey(meshInfo.MeshId))
            {
                return;
            }

            meshInfo.PriorityHint = Time.frameCount;
            m_MeshesNeedingGeneration[meshInfo.MeshId] = meshInfo;
        }

        void CheckHeadTrackingMapEvents()
        {
            if (!headDevice.isValid)
            {
                headDevice = InputSubsystem.Utils.FindMagicLeapDevice(InputDeviceCharacteristics.HeadMounted | InputDeviceCharacteristics.TrackedDevice);
            }

            if (headDevice.isValid && InputSubsystem.Extensions.MLHeadTracking.TryGetMapEvents(headDevice, out var mapEvents))
            {
                if ((uint)(mapEvents & InputSubsystem.Extensions.MLHeadTracking.MapEvents.NewSession) != 0)
                {
                    // clear all the meshes if headtracking is starting a new session 
                    DestroyAllMeshes();
                }
            }
        }

        void UpdateSettings()
        {
            DestroyAllMeshes();
            UpdateBatchSize();

            var settings = GetMeshingSettings();
            MeshingSubsystem.Extensions.MLMeshing.Config.meshingSettings = settings;
            MeshingSubsystem.Extensions.MLMeshing.Config.density = density;

            m_SettingsDirty = false;
#if UNITY_EDITOR
            m_CachedSettings = settings;
            m_CachedDensity = density;
#endif
        }

        void UpdateBounds()
        {
            MeshingSubsystem.Extensions.MLMeshing.Config.SetBounds(transform, boundsExtents);
            transform.hasChanged = false;
        }

        void UpdateBatchSize()
        {
            MeshingSubsystem.Extensions.MLMeshing.Config.batchSize = batchSize;
        }

        // Every frame, poll the MeshSubsystem for mesh updates (Added, Updated, Removed)
        // If the mesh is Added or Updated, then add it to the generation queue.
        //
        // Create generation requests for each mesh needing it until all have
        // been added to the asynchronous queue, or the queue is full.
        void Update()
        {

            if (m_MeshSubsystem == null)
                return;
            if (!m_MeshSubsystem.running)
                return;
#if UNITY_EDITOR
            m_SettingsDirty |= haveSettingsChanged;
#endif
            CheckHeadTrackingMapEvents();

            if (m_SettingsDirty)
                UpdateSettings();

            if (transform.hasChanged)
                UpdateBounds();

            // Since meshing is a two pass asynchronous API, we need to poll at twice the configured rate.
            // Once to request the mesh info, and a second time to request the associated mesh blocks. 
            // If a block request is pending, a new mesh info request will not be made, the inverse is also true.
            // Polling at twice the rate will ensure that data appears at the desired interval.  
            float timeSinceLastUpdate = (float)(DateTime.Now - m_TimeLastUpdated).TotalSeconds;
            bool allowUpdate = (timeSinceLastUpdate > (m_PollingRate / 2.0f));
            bool meshes = m_MeshSubsystem.TryGetMeshInfos(meshInfos);
            if (allowUpdate && meshes)
            {
                int i = 0;
                foreach (var meshInfo in meshInfos)
                {
                    i++;

                    switch (meshInfo.ChangeState)
                    {
                        case MeshChangeState.Added:
                        case MeshChangeState.Updated:
                            AddToQueueIfNecessary(meshInfo);
                            break;

                        case MeshChangeState.Removed:
                            RaiseMeshRemoved(meshInfo.MeshId);

                            // Remove from processing queue
                            m_MeshesNeedingGeneration.Remove(meshInfo.MeshId);

                            // Destroy the GameObject
                            GameObject meshGameObject;
                            if (meshIdToGameObjectMap.TryGetValue(meshInfo.MeshId, out meshGameObject))
                            {
                                Destroy(meshGameObject);
                                meshIdToGameObjectMap.Remove(meshInfo.MeshId);
                            }
                            break;

                        default:
                            break;
                    }
                }

                m_TimeLastUpdated = DateTime.Now;
            }

            if (meshPrefab != null)
            {
                MeshId meshId;
                while (m_MeshesBeingGenerated.Count < meshQueueSize && GetNextMeshToGenerate(out meshId))
                {
                    GameObject meshGameObject = GetOrCreateGameObject(meshId);
                    var meshCollider = meshGameObject.GetComponent<MeshCollider>();
                    var meshFilter = meshGameObject.GetComponent<MeshFilter>();
                    var mesh = GetOrCreateMesh(meshFilter);
                    var meshAttributes = computeNormals ? MeshVertexAttributes.Normals : MeshVertexAttributes.None;
                    m_MeshSubsystem.GenerateMeshAsync(meshId, mesh, meshCollider, meshAttributes, OnMeshGenerated);
                    m_MeshesBeingGenerated.Add(meshId, m_MeshesNeedingGeneration[meshId]);
                    m_MeshesNeedingGeneration.Remove(meshId);
                }
            }
        }

        Mesh GetOrCreateMesh(MeshFilter meshFilter)
        {
            if (meshFilter == null)
                return null;

            if (meshFilter.sharedMesh != null)
                return meshFilter.sharedMesh;

            return meshFilter.mesh;
        }

        // Find the oldest one. Prioritize new ones.
        bool GetNextMeshToGenerate(out MeshId meshId)
        {
            Nullable<KeyValuePair<MeshId, MeshInfo>> highestPriorityPair = null;
            foreach (var pair in m_MeshesNeedingGeneration)
            {
                // Skip meshes currently being generated
                if (m_MeshesBeingGenerated.ContainsKey(pair.Key))
                    continue;

                if (!highestPriorityPair.HasValue)
                {
                    highestPriorityPair = pair;
                    continue;
                }

                var consideredMeshInfo = pair.Value;
                var selectedMeshInfo = highestPriorityPair.Value.Value;

                // If the selected change type is less than this one,
                // then ignore entirely.
                if (consideredMeshInfo.ChangeState > selectedMeshInfo.ChangeState)
                    continue;

                // If this info has a higher priority change type
                // (e.g. Added rather than Updated) use it instead.
                if (consideredMeshInfo.ChangeState < selectedMeshInfo.ChangeState)
                {
                    highestPriorityPair = pair;
                    continue;
                }

                // If changeTypes are the same, but this one is older,
                // then use it.
                if (consideredMeshInfo.PriorityHint < selectedMeshInfo.PriorityHint)
                {
                    highestPriorityPair = pair;
                    continue;
                }
            }

            if (highestPriorityPair.HasValue)
            {
                meshId = highestPriorityPair.Value.Key;
                return true;
            }
            else
            {
                meshId = MeshId.InvalidId;
                return false;
            }
        }

        void OnMeshGenerated(MeshGenerationResult result)
        {
            if (result.Status == MeshGenerationStatus.Success)
            {
                // The mesh may have been removed by external code
                MeshInfo meshInfo;
                if (!m_MeshesBeingGenerated.TryGetValue(result.MeshId, out meshInfo))
                    return;

                m_MeshesBeingGenerated.Remove(result.MeshId);
                switch (meshInfo.ChangeState)
                {
                    case MeshChangeState.Added:
                        RaiseMeshAdded(result.MeshId);
                        break;
                    case MeshChangeState.Updated:
                        RaiseMeshUpdated(result.MeshId);
                        break;

                    // Removed/unchanged meshes don't get generated.
                    default:
                        break;
                }

                GameObject meshGameObject = null;
                if (meshIdToGameObjectMap.TryGetValue(result.MeshId, out meshGameObject))
                {
                    // Disable the collision mesh if we're in point cloud mode
                    var meshCollider = meshGameObject.GetComponent<MeshCollider>();
                    if (meshCollider != null)
                    {
                        meshCollider.enabled = currentMeshType != MeshType.PointCloud;
                    }
                }
            }
            else
            {
                m_MeshesBeingGenerated.Remove(result.MeshId);
            }
        }

        void RaiseMeshAdded(MeshId meshId)
        {
            if (meshAdded != null)
                meshAdded(meshId);
        }

        void RaiseMeshUpdated(MeshId meshId)
        {
            if (meshUpdated != null)
                meshUpdated(meshId);
        }

        void RaiseMeshRemoved(MeshId meshId)
        {
            if (meshRemoved != null)
                meshRemoved(meshId);
        }

        bool m_SettingsDirty;

        DateTime m_TimeLastUpdated = DateTime.MinValue;

        Dictionary<MeshId, MeshInfo> m_MeshesNeedingGeneration;

        Dictionary<MeshId, MeshInfo> m_MeshesBeingGenerated;

        List<MeshInfo> meshInfos = new List<MeshInfo>();

        MagicLeapLoader m_Loader;
        XRMeshSubsystem m_MeshSubsystem;
    }
}
```




