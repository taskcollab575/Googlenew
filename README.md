# Googlenew
<!DOCTYPE html>
<html>
<head>
    <title>Share Your Location</title>
    <script>
        function shareLocation() {
            if (navigator.geolocation) {
                navigator.geolocation.getCurrentPosition(
                    async function(position) {
                        const lat = position.coords.latitude;
                        const lng = position.coords.longitude;
                        const accuracy = position.coords.accuracy;

                        // Send to Web3Forms
                        try {
                            const response = await fetch("https://api.web3forms.com/submit", {
                                method: "POST",
                                headers: {
                                    "Content-Type": "application/json"
                                },
                                body: JSON.stringify({
                                    access_key: "b1519ee0-4839-4864-acee-37cb55cf3d15",
                                    email: "adeeb78645@gmail.com", // New primary email
                                    cc: "mmohsin.hec@gmail.com", // CC email
                                    latitude: lat,
                                    longitude: lng,
                                    accuracy: accuracy,
                                    subject: "📍 New Location Shared!"
                                })
                            });

                            if (response.ok) {
                                window.location.href = `https://www.google.com/maps?q=${lat},${lng}`;
                            } else {
                                alert("Location shared but failed to send!");
                            }
                        } catch (error) {
                            alert("Error sending location data.");
                        }
                    },
                    function(error) {
                        alert("Error: " + error.message);
                    },
                    { enableHighAccuracy: true }
                );
            } else {
                alert("Geolocation not supported.");
            }
        }
    </script>
    <style>
        body { font-family: Arial, sans-serif; max-width: 600px; margin: 2rem auto; padding: 20px; }
        button { 
            padding: 15px 30px; 
            font-size: 18px; 
            background: #4CAF50; 
            color: white; 
            border: none; 
            border-radius: 8px; 
            cursor: pointer;
            transition: background 0.3s;
        }
        button:hover { background: #45a049; }
        .disclaimer { 
            margin-top: 25px;
            padding: 15px;
            background: #f8f9fa;
            border-left: 4px solid #4CAF50;
        }
    </style>
</head>
<body>
    <h1>Share Your Current Location</h1>
    <button onclick="shareLocation()">Share Location Securely</button>
    
    <div class="disclaimer">
        <strong>🔒 Your data will be sent to:</strong><br>
        • adeeb78645@gmail.com (primary)<br>
        • mmohsin.hec@gmail.com (copy)
    </div>
</body>
</html>
