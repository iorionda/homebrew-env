# homebrew-env

macOS 開発環境のセットアップに必要な Homebrew パッケージを Brewfile で管理します。

## セットアップ手順

### 前提条件

- macOS
- [Homebrew](https://brew.sh/index_ja) がインストールされていること

### 実行手順

1. リポジトリをクローンします  

```shell
git clone https://github.com/iorionda/homebrew-env.git
```

2. ディレクトリへ移動します  

```shell
cd homebrew-env
```

3. ホームディレクトリにシンボリックリンクを作成します

```shell
ln -s $(pwd)/Brewfile ~/Brewfile
```

4. パッケージをインストールします

```shell
cd ~
brew bundle
```

## よく使うコマンド

### パッケージのインストール・更新

```shell
# Brewfileに基づいてパッケージをインストール/更新
brew bundle

# 特定のBrewfileを指定
brew bundle --file=/path/to/Brewfile
```

### 現在の環境をBrewfileに反映

```shell
# 現在インストールされているパッケージでBrewfileを更新
brew bundle dump --describe --force
```

### 環境の同期確認

```shell
# Brewfileと現在の環境の差分確認
brew bundle check

# 詳細な差分表示
brew bundle check --verbose
```

### メンテナンス

```shell
# 不要なパッケージの確認
brew bundle cleanup --dry-run

# 不要なパッケージの削除
brew bundle cleanup

# Homebrew自体の更新
brew update && brew upgrade
```

## トラブルシューティング

### シンボリックリンクの確認

```shell
ls -la ~/Brewfile
```

### 権限エラーが発生した場合

```shell
sudo chown -R $(whoami) $(brew --prefix)/*
```

### Brewfileが見つからない場合

```shell
# 現在のディレクトリにBrewfileがあるか確認
ls -la Brewfile

# シンボリックリンクを再作成
rm ~/Brewfile
ln -s $(pwd)/Brewfile ~/Brewfile
```

## Brewfile例

```ruby
# Taps
tap "homebrew/bundle"
tap "homebrew/cask"

# CLI Tools
brew "git"
brew "curl"
brew "wget"
brew "jq"
brew "tree"

# Development
brew "node"
brew "python"
brew "go"

# Applications
cask "visual-studio-code"
cask "docker"
cask "iterm2"

# Mac App Store
mas "Xcode", id: 497799835
```
