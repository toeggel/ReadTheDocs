# Modules / Project Structure

## NG-14+

### Standalone Components

Standalone components are the new standard. By default go for standalone but Modules have still their relevance. Modules are still useful for example to hide certain components or to group components that are imported together all the time.

## Modules

> [!WARNING] 
> This might be a bit deprecated with the new standalone components. Folder structure probably still make sense, module probably not that much anymore.

> [!ABSTRACT]
> `CoreModule` should have only `services` and be imported only once in the `AppModule`.
`SharedModule` should have anything but `services` and be imported in all modules that need the shared stuff (which could also be the `AppModule`).

### Core

The Core should contain mainly components which are used once in the application and need to be available when the app starts. This module (and all its components) gets loaded only once, globally in AppModule (on app start). Main focus here are services used across the App since they are singletons anyway.

### Shared

The Shared Module contains all the (commonly used) components which are shared between the other components and feature modules. The components defined in the shared modules only get loaded when they are used (and might not get loaded at all).

### Feature

Feature modules house the main features of your Angular application.
Breaking an app and their functionalities into feature modules helps you split the application into dedicated areas. This allows better separation of concerns.
