# windows-env
 Windows マシンの初期セットアップをする

# OS
- Myrica Font

## Windows Settings
```powershell
# UAC 無効
Set-ItemProperty -Path ‘HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System’ -Name “EnableLUA” -Value 0

## フォルダオプション(拡張子を表示する)
Set-ItemProperty "HKCU:\Software\Microsoft\Windows\CurrentVersion\Explorer\Advanced" -name "HideFileExt" -Value 0

## フォルダオプション(隠しファイル、隠しフォルダ、隠しドライブを表示する)
Set-ItemProperty "HKCU:\Software\Microsoft\Windows\CurrentVersion\Explorer\Advanced" -name "Hidden" -Value 1

```
## Dos Profile
Windows コマンドプロンプトのデフォルトプロファイルを設定する。

```bat
reg add "HKEY_CURRENT_USER\SOFTWARE\Microsoft\Command Processor" /v AutoRun /d "@ECHO OFF & IF EXIST \"%HOMEDRIVE%%HOMEPATH%\dosprofile.cmd\" \"%HOMEDRIVE%%HOMEPATH%\dosprofile.cmd\" & ECHO ON"
```

## WSL 2 を有効にする
管理者権限で実行する。

```powershell
# Linux 用 Windows サブシステム
dism.exe /online /enable-feature /featurename:Microsoft-Windows-Subsystem-Linux /all /norestart

# 仮想マシン プラットフォーム
dism.exe /online /enable-feature /featurename:VirtualMachinePlatform /all /norestart
```

PC Restart

```powershell
# WSL 2 Kernel Update
Invoke-WebRequest -Uri https://wslstorestorage.blob.core.windows.net/wslblob/wsl_update_x64.msi -OutFile wsl_update_x64.msi -UseBasicParsing
msiexec /i wsl_update_x64.msi /passive /norestart
rm wsl_update_x64.msi

# WSL 2 を標準にする
wsl --set-default-version 2
```

# Application
## 手動でインストールする
- boostnote
- Google IME
- GEFORCE EXPERIENCE
- Logicool G HUB
- Happy Hacking Keyboardキーマップ変更ツール
- League Display
- VoiceMeeter Potato
- Philips hue Sync
- Flash Print

## Microsoft Store からインストールする
- Windows Terminal

## chocolatey でインストールする
```powershell
choco install -y choco-packages.config
choco install -y choco-packages-game.config

# App 側で自動更新があるやつは choco とバージョンがずれてしまうので pin 止めしておく
choco pin add -n=googlechrome
```

## Google Chrome addon
- AdBlock
- Dark Theme for Google
- Video Speed Controller
- Chrome Remote Desktop
- One Tab
- 1 Password
- Notion Web Clipper
