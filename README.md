# Captions
- [What is Dart and why does Flutter use it?](#what-is-dart-and-why-does-flutter-use-it)
- [Differentiate between named parameters and positional parameters in Dart?](#differentiate-between-named-parameters-and-positional-parameters-in-dart)
- [How do you check if an async void method is completed in Dart?](#how-do-you-check-if-an-async-void-method-is-completed-in-dart)
- [How is whenCompleted different from then in Future?](#how-is-whencompleted-different-from-then-in-future)
- [What are Null-aware operators?](#what-are-null-aware-operators)
- [What is ?. operator?](https://github.com/giorgi19/dart_questions#what-is-?.-operatort)
- [What's the difference between async and async* in Dart?](https://github.com/giorgi19/dart_questions#what's-the-difference-between-async-and-async*-in-dart)



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

## How is whenCompleted() different from then() in Future?

whenComplete() will fire a function either when the Future completes with an error or not, instead .then() will fire a function after the Future completes without an error. This is the asynchronous equivalent of a "finally" block.

## What are Null-aware operators?
Dart offers some handy operators for dealing with values that might be null.
- One is the ??= assignment operator, which assigns a value to a variable only if that variable is currently null:
```dart
	int a; // The initial value of a is null.
	a ??= 3;
	print(a); // <-- Prints 3.

	a ??= 5;
	print(a); // <-- Still prints 3.
```
- Another null-aware operator is ??, which returns the expression on its left unless that expression’s value is null, in which case it evaluates and returns the expression on its right:
```dart
	print(1 ?? 3); // <-- Prints 1.
	print(null ?? 12); // <-- Prints 12.
```
## What is ?. operator?
?. [Conditional member access] - Like ., but the leftmost operand can be null; example: foo?.bar selects property bar from expression foo unless foo is null (in which case the value of foo?.bar is null)

It is simply does a null check before accessing member. If left hand side of the operator is not null then it works simply as . and if it is null value then the whole thing is null.

for example:
	
_debounceTimer?.isActive 
	
if _debounceTimer is null then _debounceTimer?.isActive == null 
	
if _debounceTimer is not null then _debounceTimer?.isActive == _debounceTimer.isActive.

## What's the difference between async and async* in Dart?

### Short answer
async gives you a Future
	
async* gives you a Stream.
	
### async
You add the async keyword to a function that does some work that might take a long time. It returns the result wrapped in a Future.
```dart
Future<int> doSomeLongTask() async {
  await Future.delayed(const Duration(seconds: 1));
  return 42;
}
```
You can get that result by awaiting the Future:
```dart
main() async {
  int result = await doSomeLongTask();
  print(result); // prints '42' after waiting 1 second
}
```
### async*
You add the async* keyword to make a function that returns a bunch of future values one at a time. The results are wrapped in a Stream.
```dart
	Stream<int> countForOneMinute() async* {
  for (int i = 1; i <= 60; i++) {
    await Future.delayed(const Duration(seconds: 1));
    yield i;
  }
}
```
The technical term for this is [asynchronous generator function](https://dart.dev/guides/language/language-tour#generators). You use yield to return a value instead of return because you aren't leaving the function.

You can use await for to wait for each value emitted by the Stream.
```dart
 main() async {
  await for (int i in countForOneMinute()) {
    print(i); // prints 1 to 60, one integer per second
  }
}
```
