# Chatterbox TTS サーバー: OpenAI互換API・Web UI・長文対応・内蔵音声付き

**強力な [Chatterbox TTSモデル](https://github.com/resemble-ai/chatterbox) を FastAPIサーバーでセルフホスト！直感的なWeb UI、柔軟なAPI、音声クローン、長文分割処理、オーディオブック生成、内蔵音声・シード指定による一貫した音声生成が可能です。**

> 🚀 **今すぐ試せます！Google ColabでフルTTSサーバー（音声クローン・オーディオブック生成対応）をインストール不要で体験！**
> 
> [![Open Live Demo](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/devnen/Chatterbox-TTS-Server/blob/main/Chatterbox_TTS_Colab_Demo.ipynb)

このサーバーは [Dia-TTS-Server](https://github.com/devnen/Dia-TTS-Server) の設計・UIをベースに、`chatterbox-tts`エンジンを採用しています。NVIDIA (CUDA)、AMD (ROCm)、Apple Silicon (MPS) GPUで高速動作、CPUにも自動対応。

[![Project Link](https://img.shields.io/badge/GitHub-devnen/Chatterbox--TTS--Server-blue?style=for-the-badge&logo=github)](https://github.com/devnen/Chatterbox-TTS-Server)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg?style=for-the-badge)](LICENSE)
[![Python Version](https://img.shields.io/badge/Python-3.10+-blue.svg?style=for-the-badge)](https://www.python.org/downloads/)
[![Framework](https://img.shields.io/badge/Framework-FastAPI-green.svg?style=for-the-badge)](https://fastapi.tiangolo.com/)
[![Model Source](https://img.shields.io/badge/Model-ResembleAI/chatterbox-orange.svg?style=for-the-badge)](https://github.com/resemble-ai/chatterbox)
[![Docker](https://img.shields.io/badge/Docker-Supported-blue.svg?style=for-the-badge)](https://www.docker.com/)
[![Web UI](https://img.shields.io/badge/Web_UI-Included-4285F4?style=for-the-badge&logo=googlechrome&logoColor=white)](#)
[![CUDA Compatible](https://img.shields.io/badge/NVIDIA_CUDA-Compatible-76B900?style=for-the-badge&logo=nvidia&logoColor=white)](https://developer.nvidia.com/cuda-zone)
[![ROCm Compatible](https://img.shields.io/badge/AMD_ROCm-Compatible-ED1C24?style=for-the-badge&logo=amd&logoColor=white)](https://rocm.docs.amd.com/)
[![MPS Compatible](https://img.shields.io/badge/Apple_MPS-Compatible-000000?style=for-the-badge&logo=apple&logoColor=white)](https://developer.apple.com/metal/)
[![API](https://img.shields.io/badge/OpenAI_Compatible_API-Ready-000000?style=for-the-badge&logo=openai&logoColor=white)](https://platform.openai.com/docs/api-reference)
[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/devnen/Chatterbox-TTS-Server/blob/main/Chatterbox_TTS_Colab_Demo.ipynb)

<div align="center">
  <img src="static/screenshot-d.png" alt="Chatterbox TTS Server Web UI - Dark Mode" width="33%" />
  <img src="static/screenshot-l.png" alt="Chatterbox TTS Server Web UI - Light Mode" width="33%" />
</div>

---

## 🗣️ 概要: 強化されたChatterbox TTS生成

[Chatterbox TTSモデル（Resemble AI）](https://github.com/resemble-ai/chatterbox) は高品質な音声合成を提供します。本プロジェクトは [FastAPI](https://fastapi.tiangolo.com/) サーバーでChatterboxを簡単に使えるように拡張しています。

**🚀 すぐ試したい方:** [Google Colabデモを起動](https://colab.research.google.com/github/devnen/Chatterbox-TTS-Server/blob/main/Chatterbox_TTS_Colab_Demo.ipynb) すればインストール不要です！

サーバーはテキスト入力で音声合成を行い、以下の特徴を持ちます：

*   **モダンなWeb UI** で実験・プリセット・音声管理・パラメータ調整が簡単
*   **マルチプラットフォーム高速化**: NVIDIA (CUDA)、AMD (ROCm)、Apple Silicon (MPS) GPU対応、自動でCPUにも対応
*   **長文対応**: 長いテキストを文単位で分割し、順次処理・音声連結
*   **📚 オーディオブック生成**: 本文全体を貼り付けるだけで一貫した音声のオーディオブックを自動生成
*   **内蔵音声**: 用意された合成音声を選択可能
*   **音声クローン**: 参照音声ファイルから声質を再現
*   **一貫した生成**: 内蔵音声やクローン＋シード指定で安定した音声出力
*   **Docker対応**: 簡単に再現性のあるコンテナ展開

ChatterboxのTTS機能を安定・高品質・長文対応で活用できます。

## ✨ 主な特徴

**🔥 ライブデモあり:**
*   **🚀 [ワンクリックGoogle Colabデモ](https://colab.research.google.com/github/devnen/Chatterbox-TTS-Server/blob/main/Chatterbox_TTS_Colab_Demo.ipynb):** ブラウザだけですぐ体験可能

このサーバーは `chatterbox-tts` エンジンを以下のように拡張しています：

**🚀 コア機能:**

*   **長文分割処理（チャンク化）:**
    *   長いテキストを文単位で自動分割し、個別に音声生成・連結
    *   オーディオブック生成に最適
    *   UIでON/OFF・チャンクサイズ調整可能
*   **内蔵音声:**
    *   `./voices` ディレクトリの合成音声を選択可能
*   **音声クローン:**
    *   参照音声ファイル（.wav/.mp3）から声質を再現
*   **生成シード:**
    *   シード指定で一貫した音声生成が可能
*   **APIエンドポイント（/tts）:**
    *   テキスト・音声モード・参照/内蔵音声・分割制御・生成パラメータ・出力形式など細かく指定可能
*   **UI設定管理:**
    *   `config.yaml` の編集・保存がUIから可能
*   **設定システム:**
    *   `config.yaml` で全設定を管理。初回起動時に自動生成
*   **音声後処理（オプション）:**
    *   無音トリム・内部無音短縮・無声区間除去など（設定可能）
*   **UI状態保存:**
    *   テキスト・音声モード・ファイル選択・パラメータ等を `config.yaml` に保存

**🔧 一般的な強化点:**

*   **パフォーマンス:** GPUで高速・省メモリ
*   **Webインターフェース:** テキスト入力・パラメータ調整・音声管理・再生
*   **モデルロード:** Hugging Face Hubから自動ダウンロード
*   **依存管理:** 明確な `requirements.txt`
*   **ユーティリティ:** 音声・テキスト・ファイル処理用 `utils.py`

## ✅ 機能まとめ

*   **Chatterbox本来の機能:**
    *   🗣️ 高品質な単一話者音声合成
    *   🎤 参照音声によるクローン
*   **サーバー・API拡張:**
    *   ⚡ 高速なFastAPIフレームワーク
    *   ⚙️ `/tts` APIで細かい制御
    *   📄 Swagger UIでAPIドキュメント
    *   🩺 ヘルスチェックエンドポイント
*   **高度な生成機能:**
    *   📚 長文分割・連結
    *   📖 オーディオブック生成
    *   🎤 内蔵音声・音声クローン
    *   🌱 シード指定で一貫性
    *   🔇 音声後処理
*   **直感的なWeb UI:**
    *   🖱️ モダンUI
    *   💡 プリセット
    *   🎤 音声ファイルアップロード
    *   🗣️ 音声モード選択
    *   🎛️ パラメータ調整
    *   💾 設定保存
    *   💾 セッション保存
    *   ✂️ チャンク制御
    *   ⚠️ 警告モーダル
    *   🌓 ライト/ダークモード
    *   🔊 波形プレイヤー
    *   ⏳ ローディング表示
*   **柔軟なモデル管理:**
    *   ☁️ Hugging Face Hubから自動取得
    *   🔄 モデルリポジトリ指定可
    *   📄 事前ダウンロード用スクリプトあり
*   **パフォーマンス・設定:**
    *   💻 GPU自動判別
    *   ⚙️ 全設定は `config.yaml` で管理
    *   📦 標準Python仮想環境
*   **Docker対応:**
    *   🐳 Docker・Composeで簡単展開
    *   🔌 NVIDIA GPU対応
    *   💾 モデル・音声・出力・ログ・設定を永続化
    *   🚀 ワンコマンドで起動

## 🔩 システム要件

*   **OS:** Windows 10/11 (64bit) または Linux (Debian/Ubuntu推奨)
*   **Python:** 3.10以降 ([ダウンロード](https://www.python.org/downloads/))
*   **Git:** リポジトリ取得用 ([ダウンロード](https://git-scm.com/downloads))
*   **インターネット:** 依存・モデル取得用
*   **(推奨) GPU:**
    *   **NVIDIA:** CUDA対応 (Maxwell以降)
    *   **AMD:** ROCm対応 (RX 6000/7000等)
    *   **Apple Silicon:** M1/M2/M3以降 (macOS 12.3+)
*   **(Linuxのみ):**
    *   `libsndfile1`（`sudo apt install libsndfile1`）
    *   `ffmpeg`（`sudo apt install ffmpeg`）

## 💻 インストールとセットアップ

このプロジェクトはハードウェア別の依存ファイルで簡単インストールできます。

**1. リポジトリをクローン**
```bash
git clone https://github.com/devnen/Chatterbox-TTS-Server.git
cd Chatterbox-TTS-Server
```

**2. Python仮想環境を作成**

他プロジェクトとの競合を避けるため仮想環境を推奨します。

*   **Windows (PowerShell):**
    ```powershell
    python -m venv venv
    .\venv\Scripts\activate
    ```

*   **Linux (Bash):**
    ```bash
    python3 -m venv venv
    source venv/bin/activate
    ```
    プロンプトが `(venv)` で始まればOKです。

**3. ハードウェアに合わせてインストール**

下記から自分の環境に合うコマンドを選んでください。

---

### **オプション1: CPUのみ**

どのPCでも動作します。

```bash
pip install --upgrade pip
pip install -r requirements.txt
```

<details>
<summary><strong>💡 これはどう動くか</strong></summary>
`requirements.txt` はCPUユーザー向けに特別に作成されています。これにより、`pip` はPyTorchのCPU専用パッケージリポジトリを使用し、互換性のある `torch` と `torchvision` のバージョンが固定されます。これにより、バージョン不一致によるエラーの一般的な原因を防ぎます。
</details>

---

### **オプション2: NVIDIA GPU (CUDA)**

NVIDIA GPU搭載PC向け。事前に最新ドライバをインストールしてください。

```bash
pip install --upgrade pip
pip install -r requirements-nvidia.txt
```

**インストール後、PyTorchがGPUを認識するか確認：**
```bash
python -c "import torch; print(f'PyTorch version: {torch.__version__}'); print(f'CUDA available: {torch.cuda.is_available()}'); print(f'Device name: {torch.cuda.get_device_name(0) if torch.cuda.is_available() else None}')"
```
`CUDA available:` が `True` ならセットアップ成功です！

<details>
<summary><strong>💡 これはどう動くか</strong></summary>
`requirements-nvidia.txt` は、`pip` にPyTorchの公式CUDA 12.1パッケージリポジトリを使用するよう指示します。これにより、CUDAサポート付きの `torch` 、 `torchvision` 、 `torchaudio` の特定の互換性のあるバージョンが固定され、 `chatterbox-tts` に必要なバージョンが確実に満たされます。
</details>

---

### **オプション3: AMD GPU (ROCm)**

ROCm対応AMD GPU搭載Linux向け。

**前提:** 最新のROCmドライバがインストールされていること

```bash
pip install --upgrade pip
pip install -r requirements-rocm.txt
```

**インストール後、PyTorchがGPUを認識するか確認：**
```bash
python -c "import torch; print(f'PyTorch version: {torch.__version__}'); print(f'ROCm available: {torch.cuda.is_available()}'); print(f'Device name: {torch.cuda.get_device_name(0) if torch.cuda.is_available() else None}')"
```
`ROCm available:` が `True` ならセットアップ成功です！

<details>
<summary><strong>💡 これはどう動くか</strong></summary>
`requirements-rocm.txt` は、`pip` にPyTorchの公式ROCm 5.7パッケージリポジトリを指示します。これにより、AMDハードウェア用の正しいGPU対応ライブラリがインストールされ、安定したパフォーマンスが提供されます。
</details>

---

### **オプション4: Apple Silicon (MPS)**

Apple Silicon Mac (M1/M2/M3等)向け。macOS 12.3以降が必要です。

**ステップ1: まずPyTorchをMPS対応でインストール
```bash
pip install --upgrade pip
pip install torch torchvision torchaudio
```

**ステップ2: サーバーのMPS設定**
`config.yaml` を開き、 `device` を `mps` に設定

**ステップ3: 残りの依存をインストール**
```bash
# chatterbox-ttsを依存関係なしでインストール
pip install --no-deps git+https://github.com/resemble-ai/chatterbox.git

# サーバーのコア依存関係をインストール
pip install fastapi 'uvicorn[standard]' librosa safetensors soundfile pydub audiotsm praat-parselmouth python-multipart requests aiofiles PyYAML watchdog unidecode inflect tqdm

# 不足しているchatterbox依存関係をインストール
pip install conformer==0.3.2 diffusers==0.29.0 resemble-perth==1.0.1 transformers==4.46.3

# s3tokenizerを依存関係なしでインストール
pip install --no-deps s3tokenizer

# ONNXの互換性のあるバージョンをインストール
pip install onnx==1.16.0
```

**ステップ4: MPSデバイスの確認**
```bash
python -c "import torch; print(f'PyTorch version: {torch.__version__}'); print(f'MPS available: {torch.backends.mps.is_available()}'); print(f'Device will use: {\"mps\" if torch.backends.mps.is_available() else \"cpu\"}')"
```
`MPS available:` が `True` ならセットアップ成功です！

<details>
<summary><strong>💡 この手順が異なる理由</strong></summary>
Apple Siliconは、依存関係の競合を避けるために、特定のインストール手順を必要とします。最初にPyTorchをMPS対応でインストールし、その後他の依存関係を注意深くインストールすることで、MPSアクセラレーションが正しく機能するようにします。
</details>

---

## 🚀 ライブデモ - 今すぐ試そう！ (Google Colab)

**インストール不要ですぐ試したい方はこちら！**

[![Open Live Demo](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/devnen/Chatterbox-TTS-Server/blob/main/Chatterbox_TTS_Colab_Demo.ipynb)

### デモの利点
- ✅ **フル機能のWeb UI**
- ✅ **音声クローン**対応
- ✅ **内蔵音声**利用可能
- ✅ **長文処理**（オーディオブック向け）
- ✅ **無料のGPUアクセラレーション**（T4 GPU）
- ✅ **インストール不要**
- ✅ **全デバイス対応**（ブラウザがあればOK）

### クイックスタート:
1. **バッジをクリック**してノートブックをGoogle Colabで開く
2. **GPUランタイムを選択**: ランタイム → ランタイムのタイプを変更 → T4 GPU → 保存
3. **セル1を実行**: 依存関係をインストール（約1〜5分）
4. **セル2を実行**: サーバーを起動し、表示されるリンクからWeb UIにアクセス
5. **「Server ready! Click below」メッセージを待つ**: "localhost:8004" リンクをクリック
6. **Web UIで音声生成**: インターフェースを使って高品質なTTS音声を作成

### 注意事項:
- **初回実行時**: モデルダウンロードに数分かかる場合があります
- **セッション制限**: Colab無料枠には使用制限があります
- **本番環境**: ローカルインストールまたはDocker展開を推奨

---

*ローカルで使いたい場合は下記の手順を参照してください。*

## ⚙️ 設定

サーバーは `config.yaml` のみで設定を管理します。

*   **`config.yaml`:** プロジェクトルートにあり、全設定・モデルパス・生成デフォルト・UI状態を保存。初回起動時に自動生成。
*   **UI設定:** Web UIの「サーバー設定」「生成パラメータ」から直接編集・保存可能。

**主な設定項目（`config.yaml` またはUIで編集）：**

*   `server`: `host`, `port`, ログ設定
*   `model`: `repo_id`（例: "ResembleAI/chatterbox"）
*   `tts_engine`: `device`（'auto', 'cuda', 'mps', 'cpu'）、音声パス等
*   `paths`: モデルキャッシュ・出力先
*   `generation_defaults`: 生成パラメータ初期値
*   `audio_output`: 出力形式・サンプリングレート等
*   `ui_state`: UIの直近状態
*   `ui`: タイトル・言語選択表示等
*   `debug`: 中間音声保存

⭐ **注意:** `server`や`model`等の変更はサーバー再起動が必要です。

## ▶️ サーバーの起動

**初回起動時のモデルダウンロードについて：**

初回起動時はHugging Face Hubからモデルファイルを自動ダウンロードします（数GB・数分かかる場合あり）。2回目以降はキャッシュを利用し高速起動。

1.  仮想環境を有効化
2.  サーバー起動：
    ```bash
    python server.py
    ```
3.  ブラウザで `http://localhost:PORT` にアクセス
4.  APIドキュメントは `http://localhost:PORT/docs`
5.  停止は `CTRL+C`

## 🔄 最新版へのアップデート

`git stash`による安全なアップデート方法と、手動バックアップの2通りを紹介します。どちらも`config.yaml`は保持されます。

**1. プロジェクトディレクトリに移動し仮想環境を有効化**

```bash
cd Chatterbox-TTS-Server
# Windows:
.\venv\Scripts\activate
# Linux:
source venv/bin/activate
```

---

### **方法1: Stash & Pop（推奨）**

```bash
git stash
git pull origin main
git stash pop
```

---

### **方法2: 手動バックアップ**

```bash
cp config.yaml config.yaml.backup
git pull origin main
cp config.yaml.backup config.yaml
```

---

### **最終ステップ**

1. 新しい設定項目が追加されていないか確認
2. 依存を再インストール（CPU/NVIDIA/AMD用コマンドを選択）
3. サーバーを再起動

---

## 💡 使い方

### Web UI (`http://localhost:PORT`)

*   **テキスト入力:** 台本や本の全文を貼り付けてOK。自動で分割・連結されます。
*   **音声モード:**
    *   `Predefined Voices`: 内蔵音声を選択
    *   `Voice Cloning`: 参照音声ファイルを選択
*   **プリセット:** `ui/presets.yaml` から例文・設定をロード
*   **音声管理:** 音声ファイルのインポート・リスト更新
*   **生成パラメータ:** 温度・誇張・CFG・速度・シード等を調整
*   **チャンク制御:** 長文時の分割ON/OFF・サイズ調整
*   **サーバー設定:** `config.yaml`の一部をUIから編集
*   **音声再生:** 波形付きプレイヤー

### APIエンドポイント（詳細は `/docs`）

主なエンドポイントは `/tts` です。

*   **`/tts` (POST):** 音声生成
    *   **リクエスト:** テキスト・音声モード・内蔵/参照音声・分割・生成パラメータ等
    *   **レスポンス:** 音声ストリーム
*   **`/v1/audio/speech` (POST):** OpenAI互換
*   **補助エンドポイント:** 設定保存・リスト取得・ファイルアップロード等

# 🐳 Docker導入

Chatterbox TTSサーバーはDockerでも簡単に動作します。ComposeファイルでGPU種別ごとに管理できます。

## 前提条件

*   [Docker](https://docs.docker.com/get-docker/) インストール済み
*   [Docker Compose](https://docs.docker.com/compose/install/) インストール済み
*   **(GPU利用時)**
    *   **NVIDIA:** 最新ドライバ・[NVIDIA Container Toolkit](https://docs.nvidia.com/datacenter/cloud-native/container-toolkit/install-guide.html)
    *   **AMD:** [ROCmドライバ](https://rocm.docs.amd.com/projects/install-on-linux/en/latest/)（Linuxのみ）

## Docker Composeの使い方（推奨）

### 1. リポジトリをクローン
```bash
git clone https://github.com/devnen/Chatterbox-TTS-Server.git
cd Chatterbox-TTS-Server
```

### 2. ハードウェアに合わせて起動

#### **NVIDIA GPU:**
```bash
docker compose up -d --build
```

#### **AMD ROCm GPU (Linuxのみ):**
```bash
docker compose -f docker-compose-rocm.yml up -d --build
```

#### **CPUのみ:**
```bash
docker compose -f docker-compose-cpu.yml up -d --build
```

### 3. アプリにアクセス
ブラウザで `http://localhost:PORT` へ

### 4. GPU認識確認

#### **NVIDIA GPU:**
```bash
docker compose exec chatterbox-tts-server nvidia-smi
docker compose exec chatterbox-tts-server python3 -c "import torch; print(f'CUDA available: {torch.cuda.is_available()}'); print(f'GPU count: {torch.cuda.device_count()}')"
```

#### **AMD ROCm GPU:**
```bash
docker compose -f docker-compose-rocm.yml exec chatterbox-tts-server rocm-smi
docker compose -f docker-compose-rocm.yml exec chatterbox-tts-server python3 -c "import torch; print(f'ROCm available: {torch.cuda.is_available()}'); print(f'Device name: {torch.cuda.get_device_name(0) if torch.cuda.is_available() else \"No GPU detected\"}')"
```

### 5. ログ・管理
```bash
# ログ確認
docker compose logs -f                                    # NVIDIA用
docker compose -f docker-compose-rocm.yml logs -f         # AMD用
docker compose -f docker-compose-cpu.yml logs -f          # CPU用

# コンテナ停止
docker compose down                                       # NVIDIA用
docker compose -f docker-compose-rocm.yml down            # AMD用
docker compose -f docker-compose-cpu.yml down             # CPU用

# コンテナ再起動
docker compose restart chatterbox-tts-server              # NVIDIA用
docker compose -f docker-compose-rocm.yml restart chatterbox-tts-server # AMD用
docker compose -f docker-compose-cpu.yml restart chatterbox-tts-server # CPU用
```

## AMD ROCmサポート詳細

### **GPUアーキテクチャの手動指定（上級者向け）**

ROCm非公式対応GPUの場合、環境変数でアーキテクチャを上書きできます：

```bash
# RX 6000/7000系: gfx1030/1100
HSA_OVERRIDE_GFX_VERSION=10.3.0 docker compose -f docker-compose-rocm.yml up -d
HSA_OVERRIDE_GFX_VERSION=11.0.0 docker compose -f docker-compose-rocm.yml up -d
# Vega系: gfx906
HSA_OVERRIDE_GFX_VERSION=9.0.6 docker compose -f docker-compose-rocm.yml up -d
```

**対応GPU一覧・詳細は公式ドキュメント参照**

## トラブルシューティング

*   **NVIDIA GPU:** `nvidia-smi`やContainer Toolkit確認、OOM時は他アプリ終了・チャンクサイズ縮小
*   **AMD ROCm:** ドライバ・グループ・アーキテクチャ指定確認
*   **Apple Silicon:** macOS 12.3+・PyTorch/MPS対応バージョン・ONNXバージョン確認
*   **一般:** ポート競合・依存エラー・権限エラー・ディスク容量等

## 設定とボリューム

*   **設定:** `config.yaml`をローカルで編集し、再起動で反映
*   **ボリューム:** 音声・参照音声・出力・ログ・モデルキャッシュ等を永続化

## 🔍 よくある質問

*   **Apple Silicon:** MPS認識・依存バージョン・ONNXバージョン・`device: mps`設定
*   **CUDA未認識/遅い:** ドライバ・PyTorchバージョン確認
*   **VRAM不足:** GPU要件・他アプリ終了・チャンクサイズ縮小
*   **Importエラー:** 仮想環境有効化・依存インストール確認
*   **libsndfileエラー:** `sudo apt install libsndfile1`
*   **モデルDL失敗:** ネット接続・`model.repo_id`確認
*   **音声クローン/内蔵音声:** ファイル配置・サーバーログ確認
*   **権限エラー:** 各ディレクトリの書き込み権限
*   **UI設定保存不可:** ブラウザキャッシュ・`config.yaml`権限
*   **ポート競合:** 他プロセス停止・`server.port`変更
*   **キャンセルボタン:** UI側のみ即時反映、バックエンド推論は停止しません

### 複数GPU環境でのGPU選択

`CUDA_VISIBLE_DEVICES` 環境変数で使用GPUを指定できます。

*   **例:**
    *   Linux/macOS: `CUDA_VISIBLE_DEVICES="1" python server.py`
    *   Windows CMD: `set CUDA_VISIBLE_DEVICES=1 && python server.py`
    *   Windows PowerShell: `$env:CUDA_VISIBLE_DEVICES="1"; python server.py`

---

## 🤝 コントリビュート

バグ報告・機能提案・プルリク大歓迎です！

## 📜 ライセンス

本プロジェクトは **MITライセンス** です。

[https://opensource.org/licenses/MIT](https://opensource.org/licenses/MIT)

## 🙏 謝辞

*   **コアモデル:** [Chatterbox TTS model](https://github.com/resemble-ai/chatterbox) by [Resemble AI](https://www.resemble.ai/)
*   **UIインスピレーション:** [Lex-au](https://github.com/Lex-au) の [Orpheus-FastAPI](https://github.com/Lex-au/Orpheus-FastAPI)
*   **類似プロジェクト:** [Dia-TTS-Server](https://github.com/devnen/Dia-TTS-Server)
*   **コンテナ技術:** [Docker](https://www.docker.com/), [NVIDIA Container Toolkit](https://github.com/NVIDIA/nvidia-docker)
*   **主要ライブラリ:**
    *   [FastAPI](https://fastapi.tiangolo.com/)
    *   [Uvicorn](https://www.uvicorn.org/)
    *   [PyTorch](https://pytorch.org/)
    *   [Hugging Face Hub](https://huggingface.co/docs/huggingface_hub/index) & [SafeTensors](https://github.com/huggingface/safetensors)
    *   [Descript Audio Codec (DAC)](https://github.com/descriptinc/descript-audio-codec)
    *   [SoundFile](https://python-soundfile.readthedocs.io/) & [libsndfile](http://www.mega-nerd.com/libsndfile/)
    *   [Jinja2](https://jinja.palletsprojects.com/)
    *   [WaveSurfer.js](https://wavesurfer.xyz/)
    *   [Tailwind CSS](https://tailwindcss.com/) (CDN経由)
