# Grafana ve Loki 
Loki veri kaynaklı ve URL ile panel üreten bir istek:

Grafana içinde Configuration -> API Keys içinde yeni bir API anahtarını "Admin" yetkisiyle oluşturacağız.

```
eyJrIjoi.....JuIjoicGFuZWxfY3JlYXRvciIsImlkIjoxfQ==
```

Aşağıdaki curl isteğiyle bir panel oluşturup içinde Loki veri kaynağından şu süzgüye göre `{filename=\"/var/log/dummy/dummy.log\"} |= ``"` günlükleri görüntüleyecek.

`-H "Authorization: Bearer ...." ` gibi bir header eklenir


```shell
export DASHBOARD_NAME="Loki Logs Dashboard"
export PANEL_NAME="Panel 1"

curl -X POST http://localhost:3000/api/dashboards/db \
-H "Content-Type: application/json" \
<<<<<<< HEAD
=======
-H "Authorization: Bearer buraya_token_gelir" \
>>>>>>> f2ec24a (token'ı siliyorum aksi halde kabul etmiyor github)
-d '{
  "dashboard": {
    "id": null,
    "title": "'"${DASHBOARD_NAME}"'",
    "panels": [
      {
        "gridPos": {
          "x": 0,
          "y": 0,
          "w": 12,
          "h": 8
        },
        "type": "logs",
        "title": "'"${PANEL_NAME}"'",
        "datasource": {
          "type": "loki",
          "uid": "P8E80F9AEF21F6940"
        },
        "targets": [
          {
            "refId": "A",
            "key": "Q-b85282c3-815a-42e8-908d-d19ce727c46a-0",
            "editorMode": "builder",
            "expr": "{filename=\"/var/log/dummy/dummy.log\"} |= ``",
            "queryType": "range",
            "datasource": {
              "type": "loki",
              "uid": "P8E80F9AEF21F6940"
            }
          }
        ],
        "options": {
          "showTime": false,
          "showLabels": false,
          "showCommonLabels": false,
          "wrapLogMessage": false,
          "prettifyLogMessage": false,
          "enableLogDetails": true,
          "dedupStrategy": "none",
          "sortOrder": "Descending"
        },
        "id": 1
      }
    ]
  },
  "overwrite": false
}'
```