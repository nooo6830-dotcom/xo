[app.py](https://github.com/user-attachments/files/22055511/app.py)
import 'package:flutter/material.dart';

void main() {
  runApp(XOApp());
}

class XOApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: 'أبو ربع XO',
      theme: ThemeData(
        primarySwatch: Colors.blueGrey,
      ),
      home: XOGamePage(),
    );
  }
}

class XOGamePage extends StatefulWidget {
  @override
  _XOGamePageState createState() => _XOGamePageState();
}

class _XOGamePageState extends State<XOGamePage> {
  List<List<String>> board = List.generate(3, (_) => List.generate(3, (_) => ''));
  String currentPlayer = 'X';
  String statusMessage = 'الدور: X';

  void resetGame() {
    setState(() {
      board = List.generate(3, (_) => List.generate(3, (_) => ''));
      currentPlayer = 'X';
      statusMessage = 'الدور: $currentPlayer';
    });
  }

  bool checkWinner() {
    // Rows and Columns
    for (int i = 0; i < 3; i++) {
      if (board[i][0] == currentPlayer &&
          board[i][1] == currentPlayer &&
          board[i][2] == currentPlayer) {
        return true;
      }
      if (board[0][i] == currentPlayer &&
          board[1][i] == currentPlayer &&
          board[2][i] == currentPlayer) {
        return true;
      }
    }
    // Diagonals
    if (board[0][0] == currentPlayer &&
        board[1][1] == currentPlayer &&
        board[2][2] == currentPlayer) {
      return true;
    }
    if (board[0][2] == currentPlayer &&
