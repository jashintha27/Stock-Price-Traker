<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Stock Price Tracker</title>
</head>
<body>
    <div id="stockPrices"></div>

    <script src="/socket.io/socket.io.js"></script>
    <script>
        const socket = io();

        socket.on('stockPriceUpdate', function(stockData) {
            const stockPrices = document.getElementById('stockPrices');
            stockPrices.innerHTML = '';
            stockData.forEach(stock => {
                const stockDiv = document.createElement('div');
                stockDiv.textContent = `${stock.symbol}: $${stock.price}`;
                stockPrices.appendChild(stockDiv);
            });
        });
    </script>
</body>
</html>

