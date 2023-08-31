import 'package:flutter/material.dart';

void main() {
  runApp(
    MaterialApp(
      debugShowCheckedModeBanner: false,
      home: Scaffold(
        appBar: AppBar(
          centerTitle: true,
          // ignore: prefer_const_constructors
          title: Text("I Am Rich"),
          backgroundColor: Colors.blueGrey[900],
        ),
        backgroundColor: Colors.blueGrey[600],
        body: Center(
          child: MyImage(),
        ),
      ),
    ),
  );
}

// ignore: use_key_in_widget_constructors
class MyImage extends StatefulWidget {
  @override
  // ignore: library_private_types_in_public_api
  _MyImageState createState() => _MyImageState();
}

class _MyImageState extends State<MyImage> {
  double _size = 50.0;
  bool _large = false;

  void _updateSize() {
    setState(() {
      _size = _large ? 450.0 : 200.0;
      _large = !_large;
    });
  }

  @override
  Widget build(BuildContext context) {
    return GestureDetector(
      onTap: () => _updateSize(),
      child: AnimatedSize(
        curve: Curves.fastOutSlowIn,
        duration: const Duration(seconds: 1),
        child: Image.asset(
          'assets/ruby.png',
          width: _size,
          height: _size,
        ),
      ),
    );
  }
}
