# SceneComponent

`SceneComponent` is the base class for components that are attached to scenes.

It derives from `AssetComponent` and is restricted to scene assets. If your component only needs to work with scenes, inheriting from `SceneComponent` is the simplest option.

```csharp
public class MusicComponent : SceneComponent { }
```

## SceneComponent vs AssetComponent

`AssetComponent` is the general base class for components and can be used with supported asset types such as `ScriptableObject` assets and scenes.

`SceneComponent` specializes `AssetComponent` for scenes and adds scene-specific APIs such as `loadedScene`, `sceneAsset`, `OnSceneLoaded()` and `OnSceneUnloaded()`.

Use `SceneComponent` when your component only needs to support scenes:

```csharp
public class LightingComponent : SceneComponent { }
```

Use `AssetComponent` when your component should support other asset types:

```csharp
public class MetadataComponent : AssetComponent { }
```

By default, an `AssetComponent` can be added to any supported asset type.

## Restricting supported asset types

Use `CanAddToAttribute` to restrict which asset types an `AssetComponent` can be added to.

```csharp
[CanAddTo(typeof(MySettings))]
public class SettingsComponent : AssetComponent { }
```

Multiple asset types can be specified:

```csharp
[CanAddTo(typeof(MySettings), typeof(MyDatabase))]
public class DataComponent : AssetComponent { }
```

Scene support can be combined with asset types:

```csharp
[CanAddTo(typeof(MySettings), scenes = true)]
public class HybridComponent : AssetComponent { }
```

If your component only supports scenes, inheriting from `SceneComponent` is usually simpler than using `CanAddToAttribute` directly.

## Lifecycle

All asset components can respond to the game lifecycle:

```csharp
public override void OnGameStart() { }
public override void OnGameQuit() { }
```

Scene components additionally receive callbacks when their owning scene is loaded or unloaded:

```csharp
public override void OnSceneLoaded() { }
public override void OnSceneUnloaded() { }
```

These methods are invoked automatically by Scene Components.

## Scene access

Every `AssetComponent` has access to its owning asset through the `asset` property.

```csharp
var asset = asset;
```

For `SceneComponent`, the owning scene can also be accessed through `loadedScene`.

```csharp
var scene = loadedScene;
```

If the scene is not currently loaded, `loadedScene` returns an invalid Unity `Scene` struct.

In the editor, `sceneAsset` can be used to access the corresponding `SceneAsset`.

## AssetComponent members

| Member | Description |
| --- | --- |
| `asset` | Gets the asset that owns this component. |
| `enabled` | Gets or sets whether the component is enabled. |
| `canBeDisabled` | Determines whether the component can be disabled. |
| `OnGameStart()` | Called when the game starts. |
| `OnGameQuit()` | Called when the game quits. |
| `IsValidComponentType(Type type)` | Gets whether a type is a valid `AssetComponent` type. |
| `Menu(DropdownMenu menu)` <img src="https://img.shields.io/badge/Editor_API-blue?logo=unity" alt="Editor" title="Used only by the Unity Editor. Does not need to be wrapped in #if UNITY_EDITOR." /> | Adds items to the component inspector menu. |
| `CreateHeader()` <img src="https://img.shields.io/badge/Editor_API-blue?logo=unity" alt="Editor" title="Used only by the Unity Editor. Does not need to be wrapped in #if UNITY_EDITOR." /> | Creates custom UI displayed above the component inspector. |
| `CreateFooter()` <img src="https://img.shields.io/badge/Editor_API-blue?logo=unity" alt="Editor" title="Used only by the Unity Editor. Does not need to be wrapped in #if UNITY_EDITOR." /> | Creates custom UI displayed below the component inspector. |

## SceneComponent members

| Member | Description |
| --- | --- |
| `loadedScene` | Gets the loaded Unity `Scene` associated with this component. |
| `sceneAsset` <img src="https://img.shields.io/badge/Editor_Only-orange?logo=unity" alt="Editor" title="Only available in the Unity Editor. Must be wrapped in #if UNITY_EDITOR." /> | Gets the scene asset associated with this component. |
| `OnSceneLoaded()` | Called when the owning scene is loaded. |
| `OnSceneUnloaded()` | Called when the owning scene is unloaded. |

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
