<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Blocksi Detection</title>
    <script>
        // Function to detect Blocksi
        function detectBlocksi() {
            // Check if Blocksi is injecting a specific script or modifying the page
            if (window.BlocksiDetected || document.body.innerHTML.includes("Blocked by Blocksi")) {
                return true;
            }
            return false;
        }

        // Function to send a notification via a webhook
        function sendNotification(message) {
            // Replace with your webhook URL
            fetch('https://your-webhook-url-here.com', {
                method: 'POST',
                headers: {
                    'Content-Type': 'application/json',
                },
                body: JSON.stringify({
                    text: message,
                }),
            })
            .then(response => {
                console.log('Notification sent:', response);
            })
            .catch(error => {
                console.error('Error sending notification:', error);
            });
        }

        // Function to check Blocksi and send notification if detected
        function checkAndNotify() {
            if (detectBlocksi()) {
                sendNotification("Blocksi has been detected on the page!");
            }
        }

        // Run the check when the page is loaded
        window.onload = checkAndNotify;
    </script>
</head>
<body>
    <h1>ODDS SCRIPT INJECTOR</h1>
    <p>This page is checking for Blocksi...</p>
</body>
</html>
