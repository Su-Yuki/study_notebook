# tmuxチートシート

|コマンド	|機能|
----|---- 
|tmux / tmux new-session -s <name>	|新規セッションの開始|
|C-b + $	|セッション名変更|
|C-b + ,	|ウィンドウ名変更|
|C-b + d	|セッションのデタッチ|
|tmux a / tmux a -t <session-name>	|セッションにアタッチ|
|tmux ls	|セッション一覧|
|tmux kill-session -t <session-name>	|セッションを削除|
|C-b + c	|ウィンドウ作成|
|C-b + n	|ウィンドウ移動（next）|
|C-b + p	|ウィンドウ移動（pre）|
|C-b + w	|ウィンドウ一覧表示で移動|
|C-b + &	|ウィンドウ強制終了|
|C-b + “	|ペイン横分割|
|C-b + %	|ペイン縦分割|
|C-b + o	|ペインの移動|
|C-b + q + <number>	|ペインのインジケータ表示・移動|
|C-b + x	|ペイン強制終了|

|コマンド	|機能|
----|---- 
|tmux split-window -v -p <number>| ペイン|
|tmux split-window -h -p <number>| ペイン|