# shake_detector

A flutter package to detect phone shakes, upgraded version on shake.

## Usage

### 1. Use as Widget
```dart 
class HomePage extends StatelessWidget {
  const HomePage({super.key});

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: const Text('ShakeGesture Example')),
      body: Center(
        // The start.
        child: ShakeDetectWrap(
          onShake: () {
            ScaffoldMessenger.of(context).showSnackBar(
              const SnackBar(content: Text('Shake!')),
            );
          },
          child: const Center(
            child: OutlinedButton(
              onPressed: ShakeGestureTestHelperExtension.simulateShake,
              child: Text('Simulate Shake'),
            ),
          ),
        ),
		// The end.
      ),
    );
  }
}

```

### 2. Use as Listener

To listen to phone shake:

```dart
ShakeDetector detector = ShakeDetector.autoStart(
    onPhoneShake: () {
        // Do stuff on phone shake
    }
);
```

OR

This will wait for user to call `startListening()` to start listening to phone shake:
```dart
ShakeDetector detector = ShakeDetector.waitForStart(
    onPhoneShake: () {
        // Do stuff on phone shake
    }
);

detector.startListening();

```

To stop listening:
```dart
detector.stopListening();
```


