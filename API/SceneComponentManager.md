# SceneComponentManager

`SceneComponentManager` is the central API for working with asset components.

This class manages most functionality related to components and component containers, such as discovering components, finding components across the project, and managing component lifecycles.

Most APIs for working with individual assets are exposed through the [extension methods](#extension-methods), which internally use this class. Publically `SceneComponentManager` instead provides APIs for working with components across the entire project.

The manager also handles the component lifecycle. It automatically invokes `OnGameStart()` and `OnGameQuit()` when entering and exiting Play Mode (or when the application starts and quits in a player), and `OnSceneLoaded()` and `OnSceneUnloaded()` when scenes are loaded and unloaded.

## `SceneComponentManager` members

### Events

| Member | Description |
| --- | --- |
| `onComponentsChanged` | Raised whenever components are added to or removed from an asset. |
| `GetComponents<T>()` | Gets every component of type `T` in the project. |
| `GetComponentsForAssetType<TComponent, TAsset>()` | Gets every component of type `TComponent` attached to assets of type `TAsset`. |
| `GetComponentTypes(bool includeHidden = true)`<br> <img src="https://img.shields.io/badge/Editor-blue?logo=unity" alt="Editor" title="Only available in the Unity Editor" /> | Gets all available component types. |
| `GetComponentTypesFor<T>(bool includeHidden = true)`<br> <img src="https://img.shields.io/badge/Editor-blue?logo=unity" alt="Editor" title="Only available in the Unity Editor" /> | Gets all component types that can be added to assets of type `T`. |

## Extension methods

Most interactions with asset components are performed through extension methods rather than `SceneComponentManager`. These methods are available on supported asset types and internally use the manager.

## Extension methods

| Type | Query | Modify |
| --- | --- | --- |
| `Scene` | `GetComponent<T>()`<br>`GetComponents<T>()`<br>`HasComponent<T>()` | `AddComponent<T>()`<br>`RemoveComponent()` |
| `ScriptableObject` | `GetComponent<T>()`<br>`GetComponents<T>()`<br>`HasComponent<T>()` | `AddComponent<T>()`<br>`RemoveComponent()` |
| `AssetReference` | `GetComponent<T>()`<br>`GetComponents<T>()`<br>`HasComponent<T>()` | `AddComponent<T>()`<br>`RemoveComponent()` |
| `MonoBehaviour` | `GetSceneComponent<T>()`<br>`GetSceneComponents<T>()`<br>`HasSceneComponent<T>()` | `AddSceneComponent<T>()`<br>`RemoveSceneComponent()` |