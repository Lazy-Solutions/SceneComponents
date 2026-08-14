# AssetReference

`AssetReference` represents a reference to either a Unity asset or a scene.

Unlike Unity object references, `AssetReference` can represent both assets and scenes through a single type, making it suitable for APIs that work with either.

```csharp
AssetReference asset = myScriptableObject;
AssetReference scene = myScene;
```

## AssetReference vs SceneReference

`AssetReference` is the general-purpose reference type used throughout Scene Components.

It can reference either:

- Unity assets (`ScriptableObject`, `Texture2D`, etc.)
- Scenes

`SceneReference` is a lightweight type used specifically for referencing scenes. It is exposed by `AssetReference` through the `sceneReference` property and can also be used directly when an API only works with scenes.

## Creating references

References can be created implicitly from supported types.

```csharp
AssetReference asset = myScriptableObject;
AssetReference scene = myScene;

SceneReference sceneRef = myScene;
```

In the editor, `SceneAsset` is also supported.

```csharp
AssetReference asset = mySceneAsset;
SceneReference scene = mySceneAsset;
```

## Loading assets

Object references can be loaded in both the editor and builds.

```csharp
var settings = asset.LoadAsset<MySettings>();
```

Scene references can only be resolved to `SceneAsset` in the editor.

## Scene references

`SceneReference` stores scenes by path rather than by object reference.

```csharp
SceneReference scene = "Assets/Scenes/Main Menu.unity";
```

It can also be converted directly to a loaded Unity `Scene`.

```csharp
Scene scene = sceneReference;
```

If the scene is not loaded, the returned `Scene` will be invalid.

## AssetReference members

| Member | Description |
| --- | --- |
| `sceneReference` | Gets the referenced scene. |
| `objectReference` | Gets the referenced Unity object. |
| `isValid` | Gets whether the reference is valid. |
| `name` | Gets the referenced asset name. |
| `GetAssetType()` | Gets the referenced asset type. |
| `LoadAsset()` | Loads the referenced asset. |
| `LoadAsset<T>()` | Loads the referenced asset as `T`. |
| `ToString()` | Gets the referenced asset name. |
| `path` <img src="https://img.shields.io/badge/Editor%20Only-orange?logo=unity" alt="Editor Only" title="Only available in the Unity Editor. Must be wrapped in #if UNITY_EDITOR." /> | Gets the referenced asset path. |
| `FromAssetPath(string)` <img src="https://img.shields.io/badge/Editor%20Only-orange?logo=unity" alt="Editor Only" title="Only available in the Unity Editor. Must be wrapped in #if UNITY_EDITOR." /> | Creates an `AssetReference` from an asset path. |

## SceneReference members

| Member | Description |
| --- | --- |
| `path` | Gets the scene path. |
| `name` | Gets the scene name. |
| `isValid` | Gets whether the reference is valid. |

## Implicit conversions

### AssetReference

| From | To |
| --- | --- |
| `Object` | `AssetReference` |
| `Scene` | `AssetReference` |
| `SceneReference` | `AssetReference` |
| `SceneAsset` <img src="https://img.shields.io/badge/Editor%20Only-orange?logo=unity" alt="Editor Only" title="Only available in the Unity Editor. Must be wrapped in #if UNITY_EDITOR." /> | `AssetReference` |

### SceneReference

| From | To |
| --- | --- |
| `Scene` | `SceneReference` |
| `string` | `SceneReference` |
| `SceneAsset` <img src="https://img.shields.io/badge/Editor%20Only-orange?logo=unity" alt="Editor Only" title="Only available in the Unity Editor. Must be wrapped in #if UNITY_EDITOR." /> | `SceneReference` |
| `SceneReference` | `Scene` |
| `SceneReference` | `string` |
| `SceneReference` <img src="https://img.shields.io/badge/Editor%20Only-orange?logo=unity" alt="Editor Only" title="Only available in the Unity Editor. Must be wrapped in #if UNITY_EDITOR." /> | `SceneAsset` |

## Badge legend

| Badge | Meaning |
| --- | --- |
| <img src="https://img.shields.io/badge/Editor_API-blue?logo=unity" alt="Editor API" /> | Used only by the Unity Editor. Does not need to be wrapped in `#if UNITY_EDITOR`. |
| <img src="https://img.shields.io/badge/Editor%20Only-orange?logo=unity" alt="Editor Only" /> | Only available in the Unity Editor. Must be wrapped in `#if UNITY_EDITOR`. |

<!--
Soft editor dep:
<img src="https://img.shields.io/badge/Editor_API-blue?logo=unity" alt="Editor API" title="Used only by the Unity Editor. Does not need to be wrapped in #if UNITY_EDITOR." />

Hard editor dep:
<img src="https://img.shields.io/badge/Editor%20Only-orange?logo=unity" alt="Editor Only" title="Only available in the Unity Editor. Must be wrapped in #if UNITY_EDITOR." />
-->