# C/C++ スタートアップ設定セット

Windows 上で **Visual Studio / VS Code / Claude Code を混在**させて C/C++ を開発するときの、
最初に置いておく設定ファイル一式。新しいリポジトリの雛形として使う。

## 含まれるもの

| ファイル | 役割 |
| --- | --- |
| `.gitignore` | ビルド生成物や一時ファイルを git 管理から除外(Visual Studio + DxLib 対応) |
| `.gitattributes` | 改行コードの「正」。リポ内は LF、C/C++ は CRLF でチェックアウト。バイナリを保護 |
| `.editorconfig` | エディタの文字コード・改行・インデントをそろえる(C/C++ は BOM付きUTF-8 + CRLF) |
| `.clang-format` | C/C++ の保存時整形ルール(VS / VS Code / CLion で同一表示) |
| `CLAUDE.md` | Claude Code のプロジェクトメモリ。文字化け・改行崩れを防ぐ制約などを明記 |
| `.claude/settings.json` | Claude Code の共有設定(秘匿ファイルの読み取り拒否など) |
| `.vscode/extensions.json` | 推奨拡張(C/C++・EditorConfig・Claude Code) |
| `.vscode/settings.json` | 保存時整形・clang-format 連携などの VS Code 設定 |

## 文字コード・改行の考え方(役割分担)

- **`.gitattributes`** … コミット/チェックアウト時の改行コードを機械的に強制(最終的な正)。
- **`.editorconfig`** … エディタが開く/保存するときの文字コード・改行をそろえる。
- **`.clang-format`** … 空白やインデントなど、コードの整形。

この3つで、Visual Studio・VS Code・Claude Code のどれで触っても
**文字化けや改行コードの崩れ、無駄な差分が出ない**状態にする。

## 使い方

1. このリポジトリの内容を新プロジェクトの直下にコピーする。
2. VS Code で開き、推奨拡張(特に **EditorConfig**)を入れる。
3. `CLAUDE.md` の「ビルド・テスト」欄に、そのプロジェクトの実コマンドを書く。
4. `.clang-format` の行幅やポインタ位置など、好みに合わせて調整する(コメント参照)。
