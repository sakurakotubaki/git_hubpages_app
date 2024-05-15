# github_pages_app
Flutter Webで作成したWeb PageをGithub PageへDeployします。

1. プロジェクトを作成
```bash
flutter create github_pages_app --org com.jboycode
```

2. 表示するページを作成
```dart
import 'package:flutter/material.dart';

void main() {
  runApp(const MyApp());
}

class MyApp extends StatelessWidget {
  const MyApp({super.key});

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      debugShowCheckedModeBanner: false,
      title: 'Flutter Demo',
      theme: ThemeData(
        colorScheme: ColorScheme.fromSeed(seedColor: Colors.deepPurple),
        useMaterial3: true,
      ),
      home: const MyHomePage(title: 'Flutter Web Page'),
    );
  }
}

class MyHomePage extends StatefulWidget {
  const MyHomePage({super.key, required this.title});

  final String title;

  @override
  State<MyHomePage> createState() => _MyHomePageState();
}

class _MyHomePageState extends State<MyHomePage> {
  int _counter = 0;

  void _incrementCounter() {
    setState(() {
      _counter++;
    });
  }

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        backgroundColor: Colors.blueGrey,
        title: Text(widget.title),
      ),
      floatingActionButton: FloatingActionButton(
        onPressed: _incrementCounter,
        tooltip: 'Increment',
        child: const Icon(Icons.add),
      ),
      body: Center(
        child: Column(
          mainAxisAlignment: MainAxisAlignment.center,
          children: <Widget>[
            Image.asset('assets/cat.png'),
            const SizedBox(height: 16),
            const Text(
              'お世話になっておりますネコ様',
              style: TextStyle(fontSize: 24),
            ),
            const SizedBox(height: 16),
            Text(
              'count: $_counter',
            ),
          ],
        ),
      ),
    );
  }
}
```

3. Flutter Web Deployに必要なファイルだけデプロイする。コマンドで必要なファイルを生成する。
```bash
flutter build web
```

webディレクトリにターミナルで移動する。
```bash
cd web
```

4. Gitコマンドを実行
```bash
git init
git add .
git commit -m "first commit"
```

5. Githubにpushする。