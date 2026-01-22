<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>منصة ICT الاحترافية للتحليل</title>
    <style>
        :root {
            --primary: #00ffaa; /* لون أخضر فوسفوري للسيولة */
            --bg-dark: #050505;
            --card-bg: #111111;
            --text-color: #e0e0e0;
            --border-color: #2a2a2a;
        }

        body {
            background-color: var(--bg-dark);
            color: var(--text-color);
            font-family: 'Segoe UI', Roboto, Helvetica, Arial, sans-serif;
            margin: 0;
            overflow-x: hidden;
        }

        /* رأس الموقع */
        header {
            background: var(--card-bg);
            padding: 15px 30px;
            display: flex;
            justify-content: space-between;
            align-items: center;
            border-bottom: 1px solid var(--border-color);
            position: sticky;
            top: 0;
            z-index: 1000;
        }

        .logo { font-size: 24px; font-weight: bold; color: var(--primary); text-transform: uppercase; }

        /* حاوية الأدوات */
        .dashboard {
            display: grid;
            grid-template-columns: 3fr 1fr; /* الشارت كبير والتحليل جانبي */
            gap: 15px;
            padding: 15px;
            height: calc(100vh - 80px);
        }

        .main-chart {
            background: var(--card-bg);
            border-radius: 10px;
            border: 1px solid var(--border-color);
            overflow: hidden;
            display: flex;
            flex-direction: column;
        }

        .side-panel {
            display: flex;
            flex-direction: column;
            gap: 15px;
        }

        .widget-box {
            background: var(--card-bg);
            border-radius: 10px;
            border: 1px solid var(--border-color);
            padding: 10px;
            flex: 1;
        }

        h3 { color: var(--primary); font-size: 16px; margin-top: 0; border-bottom: 1px solid #222; padding-bottom: 8px; }

        /* جعل الموقع متجاوب للهواتف */
        @media (max-width: 900px) {
            .dashboard { grid-template-columns: 1fr; height: auto; }
            .main-chart { height: 500px; }
        }
    </style>
</head>
<body>

<header>
    <div class="logo">ICT Dashboard ⚡</div>
    <div id="market-status">الأسواق: تعمل مباشر</div>
</header>

<div style="height: 40px;">
    <script type="text/javascript" src="https://s3.tradingview.com/external-embedding/embed-widget-ticker-tape.js" async>
    {
    "symbols": [
        {"proName": "FX_IDC:EURUSD", "title": "EUR/USD"},
        {"proName": "FX_IDC:GBPUSD", "title": "GBP/USD"},
        {"proName": "OANDA:XAUUSD", "title": "الذهب"},
        {"proName": "BITSTAMP:BTCUSD", "title": "البيتكوين"},
        {"proName": "OANDA:NAS100USD", "title": "نازداك"}
    ],
    "colorTheme": "dark", "isTransparent": false, "displayMode": "adaptive", "locale": "ar"
    }
    </script>
</div>

<div class="dashboard">
    <div class="main-chart">
        <div id="tv_chart_container" style="height: 100%; width: 100%;"></div>
    </div>

    <div class="side-panel">
        <div class="widget-box">
            <h3>المفكرة الاقتصادية</h3>
            <div class="tradingview-widget-container">
                <div class="tradingview-widget-container__widget"></div>
                <script type="text/javascript" src="https://s3.tradingview.com/external-embedding/embed-widget-events.js" async>
                { "colorTheme": "dark", "isTransparent": true, "width": "100%", "height": "100%", "locale": "ar", "importanceFilter": "-1,0,1" }
                </script>
            </div>
        </div>

        <div class="widget-box">
            <h3>تحليل السوق السريع</h3>
            <script type="text/javascript" src="https://s3.tradingview.com/external-embedding/embed-widget-technical-analysis.js" async>
            {
            "interval": "1h", "width": "100%", "isTransparent": true, "height": "100%",
            "symbol": "FX:EURUSD", "showIntervalTabs": true, "displayMode": "single",
            "locale": "ar", "colorTheme": "dark"
            }
            </script>
        </div>
    </div>
</div>

<script type="text/javascript" src="https://s3.tradingview.com/tv.js"></script>
<script type="text/javascript">
  new TradingView.widget({
    "autosize": true,
    "symbol": "FX:EURUSD",
    "interval": "15",
    "timezone": "Etc/UTC",
    "theme": "dark",
