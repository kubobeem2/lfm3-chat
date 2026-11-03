# LFM3チャット

Liquid AIの LFM3-1.7B をブラウザに直接埋め込んだ、zeta風のキャラチャット（非公式・オリジナルキャラのみ）。
サーバー推論なし。会話は端末の外に出ない。

## 使い方

1. サイトを開く
2. 「モデルを読み込む」を押す（初回は約1.5GBダウンロード、2回目以降はブラウザキャッシュ）
3. キャラを選んで話しかける。＋つくる で自分のキャラも作れる（localStorage保存）

## しくみ

- 既定エンジン: WebLLM 0.2.85 + `CharlZKP/LFM3-1.7B-MLC`（q6f16_a、WebGPU、shader-f16必須、context 32768）
  - 元モデル: `LiquidAI/LFM3-1.7B`（1.73B、tri-hybrid、LFM Open License v1.0）
- 代替エンジン: transformers.js 4.3.2 + `LiquidAI/LFM3-1.7B-ONNX`（q4）— 「ONNXで再試行」ボタン
- GGUF版（PCのllama.cpp用、ブラウザ版ではない）: `LiquidAI/LFM3-1.7B-GGUF`（Q4_K_M 約1.1GB、llama.cpp v0.8.0以降必須）
- 注意: wllamaの最新安定版（3.8.1、2026-10-02）はLFM3対応前なので、このサイトではGGUF経路を既定にしていない。

## 動作環境

- 推奨: PCのChrome / Edge（WebGPU + shader-f16）
- スマホはWebGPUのshader-f16対応次第で動かないことがある。その場合はPCで試すこと。
- LFM3はthinkingがデフォルトで出るため、画面では `<think>` ブロックを除去して返信だけ表示する。

## ファイル

- `index.html` — 全部入り（ビルド不要、GitHub Pagesでそのまま公開）
