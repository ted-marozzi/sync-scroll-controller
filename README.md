<!--
This README describes the package. If you publish this package to pub.dev,
this README's contents appear on the landing page for your package.

For information about how to write a good package README, see the guide for
[writing package pages](https://dart.dev/guides/libraries/writing-package-pages).

For general information about developing packages, see the Dart guide for
[creating packages](https://dart.dev/guides/libraries/create-library-packages)
and the Flutter guide for
[developing packages and plugins](https://flutter.dev/developing-packages).
-->

SyncScrollController that keeps two ScrollControllers in sync.

Similar to [LinkedScrollController](https://github.com/google/flutter.widgets/tree/master/packages/linked_scroll_controller) but has an initial offset parameter and is actively maintained.

## Features

- Initial Scroll Offset
- Accepting Pull Requests

## Getting started

In the command line

```bash
flutter pub get linked_scroll_controller
```

## Usage

```dart
import 'package:sync_scroll_controller/sync_scroll_controller.dart';


class Example extends StatefulWidget {
  const Example({ Key? key }) : super(key: key);
  @override
  State<Example> createState() => _ExampleState();
}

class _ExampleState extends State<Example> {

  late final SyncScrollControllerGroup horizontalControllers;
  late ScrollController rowsControllerHeader;
  late ScrollController rowsControllerBody;

  @override
  void initState() {
    super.initState();
    horizontalControllers = SyncScrollControllerGroup(
      initialScrollOffset: 100,
    );
    rowsControllerHeader = horizontalControllers.addAndGet();
    rowsControllerBody = horizontalControllers.addAndGet();
  }

 @override
  Widget build(BuildContext context) {
    return Column(
      children: [
        ListView(
          scrollDirection: Axis.horizontal,
          controller: rowsControllerHeader,
          children: const [
            Text(
              "Lorem Ipsum is simply dummy header of the printing",
            ),
            Text(
              "Lorem Ipsum is simply dummy header of the printing",
            ),
          ]
        ),
        ListView(
          controller: rowsControllerBody,
          scrollDirection: Axis.horizontal,
          children: const [
            Text(
              "Lorem Ipsum is simply dummy body text of the printing",
            ),
            Text(
              "Lorem Ipsum is simply dummy body text of the printing",
            ),
          ]
        )
      ]
    );
  }
}
```
