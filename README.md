# tudpu123.github.io<!DOCTYPE html>
<html lang="zh-CN">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>全国各市专属内容平台</title>
    <script src="https://cdn.jsdelivr.net/npm/qrcode@1.5.3/build/qrcode.min.js"></script>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: "PingFang SC", "Microsoft YaHei", sans-serif;
        }
        
        body {
            background-color: #f5f5f5;
            color: #333;
            line-height: 1.6;
        }
        
        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 20px;
        }
        
        header {
            text-align: center;
            padding: 30px 0;
            background: linear-gradient(135deg, #1677FF 0%, #1677FF 100%);
            color: white;
            border-radius: 10px;
            margin-bottom: 30px;
        }
        
        h1 {
            font-size: 2.2rem;
            margin-bottom: 10px;
        }
        
        .subtitle {
            font-size: 1.1rem;
            opacity: 0.9;
        }
        
        .cities-section {
            background: white;
            border-radius: 10px;
            padding: 25px;
            margin-bottom: 30px;
            box-shadow: 0 2px 10px rgba(0, 0, 0, 0.05);
        }
        
        h2 {
            font-size: 1.5rem;
            margin-bottom: 20px;
            color: #1677FF;
            border-left: 4px solid #1677FF;
            padding-left: 10px;
        }
        
        .province-group {
            margin-bottom: 25px;
        }
        
        .province-name {
            font-weight: bold;
            margin-bottom: 10px;
            color: #666;
            font-size: 1.1rem;
        }
        
        .cities-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(120px, 1fr));
            gap: 12px;
        }
        
        .city-card {
            background: #f8f9fa;
            border: 1px solid #e9ecef;
            border-radius: 6px;
            padding: 12px 8px;
            text-align: center;
            cursor: pointer;
            transition: all 0.3s ease;
        }
        
        .city-card:hover {
            background: #e6f7ff;
            border-color: #1677FF;
            transform: translateY(-2px);
            box-shadow: 0 4px 8px rgba(22, 119, 255, 0.1);
        }
        
        .city-card.selected {
            background: #e6f7ff;
            border-color: #1677FF;
            font-weight: bold;
        }
        
        .payment-section {
            background: white;
            border-radius: 10px;
            padding: 25px;
            box-shadow: 0 2px 10px rgba(0, 0, 0, 0.05);
            text-align: center;
        }
        
        .selected-city {
            font-size: 1.2rem;
            margin-bottom: 20px;
            color: #1677FF;
            font-weight: bold;
        }
        
        .price {
            font-size: 1.8rem;
            color: #ff4d4f;
            margin: 15px 0;
            font-weight: bold;
        }
        
        .qr-code-container {
            max-width: 250px;
            margin: 20px auto;
            border: 1px solid #eee;
            padding: 15px;
            border-radius: 8px;
            background: white;
        }
        
        #paymentQR {
            width: 100%;
            height: auto;
            display: block;
        }
        
        .payment-notice {
            background: #f0f8ff;
            border-left: 4px solid #1677FF;
            padding: 15px;
            margin: 20px 0;
            text-align: left;
            border-radius: 4px;
        }
        
        .steps {
            display: flex;
            justify-content: space-between;
            margin: 30px 0;
            flex-wrap: wrap;
        }
        
        .step {
            flex: 1;
            min-width: 200px;
            text-align: center;
            padding: 15px;
            margin: 10px;
        }
        
        .step-number {
            width: 40px;
            height: 40px;
            background: #1677FF;
            color: white;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            margin: 0 auto 10px;
            font-weight: bold;
        }
        
        footer {
            text-align: center;
            margin-top: 40px;
            padding: 20px;
            color: #666;
            font-size: 0.9rem;
        }
        
        .pay-button {
            background: #1677FF;
            color: white;
            border: none;
            padding: 12px 30px;
            font-size: 1.1rem;
            border-radius: 6px;
            cursor: pointer;
            transition: background 0.3s;
            margin-top: 15px;
        }
        
        .pay-button:hover {
            background: #0e60d9;
        }
        
        .pay-button:disabled {
            background: #ccc;
            cursor: not-allowed;
        }
        
        .payment-status {
            margin: 15px 0;
            padding: 10px;
            border-radius: 4px;
            font-weight: bold;
        }
        
        .status-waiting {
            background: #fff7e6;
            color: #fa8c16;
        }
        
        .status-success {
            background: #f6ffed;
            color: #52c41a;
        }
        
        .status-error {
            background: #fff2f0;
            color: #ff4d4f;
        }
        
        @media (max-width: 768px) {
            .cities-grid {
                grid-template-columns: repeat(auto-fill, minmax(100px, 1fr));
            }
            
            .steps {
                flex-direction: column;
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <header>
            <h1>全国各市专属内容平台</h1>
            <p class="subtitle">选择城市，付费获取专属优质内容</p>
        </header>
        
        <section class="cities-section">
            <h2>选择城市</h2>
            
            <div class="province-group">
                <div class="province-name">北京市</div>
                <div class="cities-grid">
                    <div class="city-card" data-city="北京市">北京市</div>
                </div>
            </div>
            
            <div class="province-group">
                <div class="province-name">广东省</div>
                <div class="cities-grid">
                    <div class="city-card" data-city="广州市">广州市</div>
                    <div class="city-card" data-city="深圳市">深圳市</div>
                    <div class="city-card" data-city="东莞市">东莞市</div>
                    <div class="city-card" data-city="佛山市">佛山市</div>
                    <div class="city-card" data-city="珠海市">珠海市</div>
                </div>
            </div>
            
            <div class="province-group">
                <div class="province-name">上海市</div>
                <div class="cities-grid">
                    <div class="city-card" data-city="上海市">上海市</div>
                </div>
            </div>
            
            <div class="province-group">
                <div class="province-name">浙江省</div>
                <div class="cities-grid">
                    <div class="city-card" data-city="杭州市">杭州市</div>
                    <div class="city-card" data-city="宁波市">宁波市</div>
                    <div class="city-card" data-city="温州市">温州市</div>
                </div>
            </div>
            
            <!-- 更多省份和城市可以继续添加 -->
        </section>
        
        <section class="payment-section">
            <h2>支付获取内容权限</h2>
            <div class="selected-city" id="selectedCityDisplay">请先选择一个城市</div>
            
            <div class="price">¥50</div>
            
            <button class="pay-button" id="payButton" disabled>生成支付二维码</button>
            
            <div class="qr-code-container" id="qrCodeContainer" style="display: none;">
                <div id="paymentQR"></div>
                <p style="margin-top: 10px; font-size: 0.9rem;">请使用支付宝或微信扫码支付</p>
            </div>
            
            <div class="payment-status" id="paymentStatus" style="display: none;"></div>
            
            <div class="payment-notice">
                <p><strong>支付说明：</strong></p>
                <p>1. 选择城市后点击"生成支付二维码"按钮</p>
                <p>2. 使用支付宝或微信扫描二维码完成支付</p>
                <p>3. 支付成功后系统将自动为您开通权限</p>
                <p>4. 如有问题，请联系在线客服</p>
            </div>
            
            <div class="steps">
                <div class="step">
                    <div class="step-number">1</div>
                    <h3>选择城市</h3>
                    <p>从上方列表中选择您要访问的城市</p>
                </div>
                <div class="step">
                    <div class="step-number">2</div>
                    <h3>生成二维码</h3>
                    <p>点击按钮生成支付二维码</p>
                </div>
                <div class="step">
                    <div class="step-number">3</div>
                    <h3>扫码支付</h3>
                    <p>使用支付宝或微信扫码完成支付</p>
                </div>
            </div>
        </section>
        
        <footer>
            <p>© 2023 全国各市专属内容平台 版权所有</p>
            <p>客服邮箱：service@example.com | 服务时间：9:00-21:00</p>
        </footer>
    </div>

    <script>
        // 配置第三方支付系统参数
        const paymentConfig = {
            apiUrl: 'https://2a.mazhifupay.com/', // 支付API地址
            pid: '131517535', // 商户ID
            key: 'dRJK919JJ8VD691Zw68n0DrDec9CJ6dn', // 商户密钥
            returnUrl: window.location.href, // 支付完成返回地址
            notifyUrl: window.location.href // 支付通知地址
        };

        let selectedCity = '';
        let paymentInterval = null;
        let tradeNo = '';

        // 城市选择功能
        document.querySelectorAll('.city-card').forEach(card => {
            card.addEventListener('click', function() {
                // 移除之前选中的样式
                document.querySelectorAll('.city-card').forEach(c => {
                    c.classList.remove('selected');
                });
                
                // 设置当前选中样式
                this.classList.add('selected');
                
                // 更新选中的城市
                selectedCity = this.getAttribute('data-city');
                document.getElementById('selectedCityDisplay').textContent = `已选择: ${selectedCity}`;
                
                // 启用支付按钮
                document.getElementById('payButton').disabled = false;
                
                // 隐藏之前的支付二维码和状态
                document.getElementById('qrCodeContainer').style.display = 'none';
                document.getElementById('paymentStatus').style.display = 'none';
                
                // 清除之前的轮询
                if (paymentInterval) {
                    clearInterval(paymentInterval);
                    paymentInterval = null;
                }
            });
        });

        // 支付按钮点击事件
        document.getElementById('payButton').addEventListener('click', function() {
            if (!selectedCity) {
                alert('请先选择一个城市');
                return;
            }
            
            // 禁用按钮防止重复点击
            this.disabled = true;
            this.textContent = '正在生成...';
            
            // 生成订单号
            tradeNo = generateTradeNo();
            
            // 调用支付API
            createPaymentOrder(selectedCity, tradeNo);
        });

        // 生成订单号
        function generateTradeNo() {
            const timestamp = new Date().getTime();
            const random = Math.floor(Math.random() * 10000);
            return `TRADE${timestamp}${random}`;
        }

        // 创建支付订单
        function createPaymentOrder(city, tradeNo) {
            // 这里应该是调用你的后端API，由后端调用第三方支付接口
            // 由于前端直接调用支付接口存在安全问题，这里使用模拟方式
            
            // 模拟API调用延迟
            setTimeout(() => {
                // 模拟支付URL（实际应由后端返回）
                const payUrl = `${paymentConfig.apiUrl}create_order?pid=${paymentConfig.pid}&key=${paymentConfig.key}&out_trade_no=${tradeNo}&money=50&city=${encodeURIComponent(city)}`;
                
                // 生成二维码
                QRCode.toCanvas(document.getElementById('paymentQR'), payUrl, function(error) {
                    if (error) {
                        console.error('生成二维码失败:', error);
                        alert('生成支付二维码失败，请重试');
                        document.getElementById('payButton').disabled = false;
                        document.getElementById('payButton').textContent = '生成支付二维码';
                        return;
                    }
                    
                    // 显示二维码容器
                    document.getElementById('qrCodeContainer').style.display = 'block';
                    
                    // 显示支付状态
                    const statusElement = document.getElementById('paymentStatus');
                    statusElement.style.display = 'block';
                    statusElement.className = 'payment-status status-waiting';
                    statusElement.textContent = '等待支付中...';
                    
                    // 恢复按钮状态
                    document.getElementById('payButton').disabled = false;
                    document.getElementById('payButton').textContent = '重新生成二维码';
                    
                    // 开始轮询支付状态
                    startPaymentStatusCheck(tradeNo);
                });
            }, 1000);
        }

        // 开始轮询支付状态
        function startPaymentStatusCheck(tradeNo) {
            // 清除之前的轮询
            if (paymentInterval) {
                clearInterval(paymentInterval);
            }
            
            // 每5秒检查一次支付状态
            paymentInterval = setInterval(() => {
                checkPaymentStatus(tradeNo);
            }, 5000);
        }

        // 检查支付状态
        function checkPaymentStatus(tradeNo) {
            // 这里应该是调用你的后端API查询支付状态
            // 由于是演示，我们使用随机结果模拟
            
            // 模拟API调用
            setTimeout(() => {
                // 模拟支付状态（实际应由后端返回）
                const status = Math.random() > 0.8 ? 'success' : 'pending';
                
                const statusElement = document.getElementById('paymentStatus');
                
                if (status === 'success') {
                    // 支付成功
                    statusElement.className = 'payment-status status-success';
                    statusElement.textContent = '支付成功！正在为您开通权限...';
                    
                    // 清除轮询
                    clearInterval(paymentInterval);
                    paymentInterval = null;
                    
                    // 支付成功后的处理
                    handlePaymentSuccess(selectedCity, tradeNo);
                } else {
                    // 仍在等待支付
                    statusElement.className = 'payment-status status-waiting';
                    statusElement.textContent = '等待支付中...';
                }
            }, 1000);
        }

        // 支付成功处理
        function handlePaymentSuccess(city, tradeNo) {
            // 这里应该调用后端API记录支付成功并开通权限
            // 模拟API调用延迟
            setTimeout(() => {
                alert(`支付成功！您已获得${city}的访问权限。`);
                
                // 这里可以跳转到城市内容页面或显示成功信息
                // window.location.href = `/city/${encodeURIComponent(city)}`;
            }, 1500);
        }

        // 页面加载完成后的初始化
        document.addEventListener('DOMContentLoaded', function() {
            // 可以添加其他初始化代码
        });
    </script>
</body>
</html>
