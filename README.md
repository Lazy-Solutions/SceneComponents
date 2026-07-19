# Scene Components for Unity

**Scene Components** is a Unity asset that lets you add Components directly to Unity assets.

Unity's Component system is one of its greatest strengths, but most Unity assets cannot normally store custom Components, data, or metadata. Developers often work around this limitation using companion ScriptableObjects, custom lookup systems, or separate configuration assets.

Scene Components extends Unity's familiar Component workflow beyond GameObjects, allowing you to attach your own custom Components to supported assets, store related data alongside them, and retrieve it through a familiar GetComponent<T>() API.

Scenes are the primary use case, allowing Unity Scene assets to store their own custom data and metadata. The same system can also be used with other supported asset types, giving your project a consistent way to organize asset-specific information.

If you've used Unity Components before, you already know how to use Scene Components.

🛒 [**Available on the Unity Asset Store**]()

## Why use Scene Components?

Scene assets are often referenced by far more than the Scene itself. Editor tools, gameplay systems, build pipelines, and custom frameworks frequently need information associated with a Scene.

With Scene Components, your Scene assets become self-describing. Instead of maintaining separate assets or lookup systems, you can attach the data directly to the Scene asset itself.

This makes it easy to store information such as:

* Gameplay configuration.
* Environment settings.
* Scene categories.
* Preview images.
* Audio settings.
* Custom project-specific data.

Since Scene Components are fully extensible, you're free to build exactly the data structures your project requires.

## Features

* Add Components directly to Unity Scene assets.
* Store custom Scene data and metadata alongside the Scene.
* Create your own custom Scene Components.
* Access components using `GetComponent<T>()` and `GetComponents<T>()`.
* Supports serialized fields, asset references, and prefab references.
* Search Unity Scene assets by the Components they contain.
* Works in both the Unity Editor and at runtime.
* Integrates with [Advanced Scene Manager](https://github.com/Lazy-Solutions/AdvancedSceneManager), extending the same Component system to Collections.

## Documentation

This documentation covers everything you need to get started with Scene Components, from creating your first custom component to building advanced editor tools and project-specific systems.

Whether you're looking to store Scene metadata, organize Unity Scene assets, or build your own Scene-based architecture, you'll find guides, examples, and API references throughout the documentation.

