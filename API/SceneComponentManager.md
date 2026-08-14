# SceneComponentManager

`SceneComponentManager` is the central static API for working with scene (and asset) components across the project.

Internally this class manages most functionality related to components and component containers.

The manager also handles the component lifecycle. It automatically invokes `OnGameStart()` and `OnGameQuit()` when entering and exiting Play Mode (or when the application starts and quits in a player), and `OnSceneLoaded()` and `OnSceneUnloaded()` when scenes are loaded and unloaded.

Most APIs for working with individual assets are exposed through the [extension methods](#extension-methods), which internally use this class. Publicly, `SceneComponentManager` instead provides APIs for working with components across the entire project.

| Member | Description |
| --- | --- |
| `onComponentsChanged` | Raised whenever components are added to or removed from an asset. |
| `GetComponents<T>()` | Gets every component of type `T` in the project. |
| `GetComponentsForAssetType<TComponent, TAsset>()` | Gets every component of type `TComponent` attached to assets of type `TAsset`. |
| `GetComponentTypes(bool includeHidden = true)` <img src="https://img.shields.io/badge/Editor%20Only-orange?logo=unity" alt="Editor" title="Only available in the Unity Editor. Must be wrapped in #if UNITY_EDITOR." /> | Gets all available component types. |
| `GetComponentTypesFor<T>(bool includeHidden = true)` <img src="https://img.shields.io/badge/Editor%20Only-orange?logo=unity" alt="Editor" title="Only available in the Unity Editor. Must be wrapped in #if UNITY_EDITOR." /> | Gets all component types that can be added to assets of type `T`. |

## Extension methods

Most interactions with asset components are performed through extension methods rather than `SceneComponentManager`. These methods are available on supported asset types and internally use the manager.

| Type | Query | Modify |
| --- | --- | --- |
| `Scene` | `GetComponent<T>()`<br>`GetComponents<T>()`<br>`HasComponent<T>()` | `AddComponent<T>()`<br>`RemoveComponent()` |
| `ScriptableObject` | `GetComponent<T>()`<br>`GetComponents<T>()`<br>`HasComponent<T>()` | `AddComponent<T>()`<br>`RemoveComponent()` |
| `AssetReference` | `GetComponent<T>()`<br>`GetComponents<T>()`<br>`HasComponent<T>()` | `AddComponent<T>()`<br>`RemoveComponent()` |
| `MonoBehaviour` | `GetSceneComponent<T>()`<br>`GetSceneComponents<T>()`<br>`HasSceneComponent<T>()` | `AddSceneComponent<T>()`<br>`RemoveSceneComponent()` |

## Badge legend
| Badge | Meaning |
| --- | --- |
| <img src="https://img.shields.io/badge/Editor_API-blue?logo=unity" alt="Editor" /> | Used only by the Unity Editor. Does not need to be wrapped in `#if UNITY_EDITOR`. |
| <img src="https://img.shields.io/badge/Editor_Only-orange?logo=unity" alt="Editor Only" /> | Only available in the Unity Editor. Must be wrapped in `#if UNITY_EDITOR`. |

<!--
Soft editor dep: 
<img src="https://img.shields.io/badge/Editor_API-blue?logo=unity" alt="Editor" title="Used only by the Unity Editor. Does not need to be wrapped in #if UNITY_EDITOR." />

Hard editor dep: 
<img src="https://img.shields.io/badge/Editor%20Only-orange?logo=unity" alt="Editor" title="Only available in the Unity Editor. Must be wrapped in #if UNITY_EDITOR." />
