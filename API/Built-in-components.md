# Built-in components

Scene Components includes a small collection of built-in components that demonstrate common patterns and provide a few useful utilities.

These components are available from the Add Component menu and can be used directly without creating a custom component.

## IDComponent

`IDComponent` provides a persistent string ID that can be used to find an asset and its components at runtime.

Each component receives an automatically generated ID, which can also be regenerated from the inspector.

```csharp
var idComponent = IDComponent.GetComponent(id);
var component = IDComponent.GetComponent<MyComponent>(id);
```

If multiple `IDComponent`s have the same ID, a warning is logged and lookup methods return the first matching component.

| Member                        | Description                                                              |
| ----------------------------- | ------------------------------------------------------------------------ |
| `id`                          | Gets or sets the ID associated with the asset.                           |
| `GenerateID()`                | Generates a new short ID.                                                |
| `GetComponent(string id)`     | Gets the `IDComponent` with the specified ID.                            |
| `GetComponent<T>(string id)`  | Gets the first component of type `T` on the asset with the specified ID. |
| `GetComponents<T>(string id)` | Gets all components of type `T` on the asset with the specified ID.      |

## LogComponent

`LogComponent` provides methods that can be called from a `UnityEvent` to log messages to the Unity Console.

The owning asset is used as the log context, making it easier to locate the asset that produced the message.

| Member                           | Description                    |
| -------------------------------- | ------------------------------ |
| `Info(string message)`           | Logs an informational message. |
| `Warning(string message)`        | Logs a warning.                |
| `Error(string message)`          | Logs an error.                 |
| `Exception(Exception exception)` | Logs an exception.             |

## NoteComponent

`NoteComponent` allows notes to be attached directly to assets.

Notes are displayed in the component inspector and can optionally use one of Unity's HelpBox icons. They are useful for documentation, reminders, or other information that should stay with an asset.

| Member | Description                                    |
| ------ | ---------------------------------------------- |
| `text` | Gets or sets the note text.                    |
| `icon` | Gets or sets the icon displayed with the note. |

## Scene event components

Scene Components includes several components that expose common scene events as `UnityEvent`s.

These events are raised in both Edit Mode and Play Mode. Persistent listeners can use Unity's call-state setting to control whether they should run in Edit Mode, Play Mode, or both.

### SceneLoadedEventComponent

Invokes a `UnityEvent` when the scene containing the component is loaded or opened.

| Member        | Description                              |
| ------------- | ---------------------------------------- |
| `sceneLoaded` | Invoked when the owning scene is loaded. |

### SceneUnloadedEventComponent

Invokes a `UnityEvent` when the scene containing the component is unloaded or closed.

| Member          | Description                                |
| --------------- | ------------------------------------------ |
| `sceneUnloaded` | Invoked when the owning scene is unloaded. |

### SceneActivatedEventComponent

Invokes a `UnityEvent` when the scene containing the component becomes the active scene.

| Member           | Description                                   |
| ---------------- | --------------------------------------------- |
| `sceneActivated` | Invoked when the owning scene becomes active. |
