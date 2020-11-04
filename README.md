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

# Application
## 手動でインストールする
- boostnote
- Google IME
- GEFORCE EXPERIENCE
- Logicool G HUB
- Happy Hacking Keyboardキーマップ変更ツール
- League Display
- VoiceMeeter BANANA

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
