# Flutter-view Widgets

> Notice: flutter_view_widgets replaces the flutter_view_tools library, which can no longer maintained due to a loss of Dart pub credentials.

> Notice: version 2.0.0 and up support null safety, and because of this may not be compatible with legacy code. Use the earlier versions if you use Dart before 2.12.

Flutter-view is a tool that lets you easily create layouts for Flutter, using Pug and Sass.

[http://flutter-view.io](http://flutter-view.io)

This package adds some widgets that allow some extra functionality for flutter-view, and are highly recommended for your flutter-view projects.

Check out the [documentation](https://docs.flutter-view.io/get-started/installation#installing-flutter-view-widgets) on how to get started with this library in your own flutter-view project.
Check out the [example project](./example) for a simple project that uses all supported widgets.

The library adds the following widgets:

## Lifecycle

A stateful widget that lets you hook into different [lifecycle events](https://flutter.io/docs/development/ui/widgets-intro#responding-to-widget-lifecycle-events) of its state, such as **initState**, **render** and **dispose**. You can use these hooks for updating and cleaning up in your view-model.

[Documentation](https://docs.flutter-view.io/reference/tag-shortcuts#lifecycle)

## ReactiveWidget

A wrapper of a Flutter **StreamWidget**, that monitors a **Listenable** such as a **[Model](https://pub.dartlang.org/documentation/scoped_model/latest/scoped_model/Model-class.html)**, and triggers an update when that **Listenable** updates. This allows for your tree of widgets to respond to model updates.

[Documentation](https://docs.flutter-view.io/reference/tag-shortcuts#reactive)
| [Usage guide](https://docs.flutter-view.io/guide/writing-reactive-code)

# Reactive mixin

It also adds the `Reactive` mixin class, that you can use to add reactive behaviors for classes that already extend a model class.

To use extend your entity classes like this:

```Dart
class MyEntity extends SomeModelClass with Reactive {
   ...
}
```

Then when listening with the [ReactiveWidget], instead of listening for
the entity itself for changes like you would with a [Model] extending class,
listen to the `.changes` property instead:
 
```Pug
some-function(flutter-view)
   reactive(watch='model.changes')
     //- code here will change when model.notifyListeners() is called
 
```
