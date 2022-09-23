# Captions
- [What is Dart and why does Flutter use it?](#what-is-dart-and-why-does-flutter-use-it?)
- [Differentiate between named parameters and positional parameters in Dart?](#named-parameters-and-positional-parameters-in-Dart)
- [How do you check if an async void method is completed in Dart?](#How-do-you-check-if-an-async-void-method-is-completed-in-dart)



## What is Dart and why does Flutter use it?

Dart is an object-oriented, garbage-collected programming language that you use to develop Flutter apps. It was also created by Google, but is open-source, and has community inside and outside Google. Dart was chosen as the language of Flutter for the following reason:

Dart is AOT (Ahead Of Time) compiled to fast, predictable, native code, which allows almost all of Flutter to be written in Dart. This not only makes Flutter fast, virtually everything (including all the widgets) can be customized.

Dart can also be JIT (Just In Time) compiled for exceptionally fast development cycles and game-changing workflow (including Flutter’s popular sub-second stateful hot reload).

Dart allows Flutter to avoid the need for a separate declarative layout language like JSX or XML, or separate visual interface builders, because Dart’s declarative, programmatic layout is easy to read and visualize. And with all the layout in one language and in one place, it is easy for Flutter to provide advanced tooling that makes layout a snap.

## Differentiate between named parameters and positional parameters in Dart?

Both named and positional parameters are part of optional parameter:

#### Optional Positional Parameters:

- A parameter wrapped by [ ] is a positional optional parameter
 ```dart
	   getHttpUrl(String server, String path, [int port=80]) {
	     // ...
	   }
 ```
 
 - You can specify multiple positional parameters for a function
 
 ```dart
	   getHttpUrl(String server, String path, [int port=80, int numRetries=3]) {
	     // ...
	   }
```
  
#### Optional Named Parameters:

- A parameter wrapped by { } is a named optional parameter.

```dart
	getHttpUrl(String server, String path, {int port = 80}) {
	  // ...
	}
```
- You can specify multiple named parameters for a function

```dart
	getHttpUrl(String server, String path, {int port = 80, int numRetries = 3}) {
	  // ...
	}
```
 
 - Because named parameters are referenced by name, they can be used in an order different from their declaration.
 
```dart
	getHttpUrl('example.com', '/index.html', numRetries: 5, port: 8080);
	getHttpUrl('example.com', '/index.html', numRetries: 5);
```

 ## How do you check if an async void method is completed in Dart?
 
 Changing the return type to Future<void>.
```dart
Future<void> questions(Question uestion) async {  
   // ...
}
```
Then you can do await questions(...); or questions().then(...);


	

  
