# Infra Monitoring

Docker + Prometheus + Grafana + Node Exporterで構築したサーバー監視システム。

## 構成

node-exporter -> prometheus -> grafana

- node-exporter: サーバーのCPU・メモリ・ディスクを数値として吐き出す
- prometheus: 15秒ごとにメトリクスを収集して保存する
- grafana: 収集したデータをグラフで可視化する

## 起動方法

docker compose up -d

## やったこと

### 意図的障害：CPU100%負荷テスト
stress-ngでCPUを意図的に100%にして、Grafanaのダッシュボードがリアルタイムで反応することを確認した。

stress-ng --cpu 2 --timeout 60s

CPU Busyのゲージが跳ね上がり、60秒後に正常値に戻ることを確認。

## アクセス先

| サービス | URL |
|---|---|
| Grafana | http://IP:3000 |
| Prometheus | http://IP:9090 |
| Nginx | http://IP:80 |
