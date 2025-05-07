# EX01 Developing a Simple Webserver
## Date:

## AIM:
To develop a simple webserver to serve html pages and display the list of protocols in TCP/IP Protocol Suite.

## DESIGN STEPS:
### Step 1: 
HTML content creation.

### Step 2:
Design of webserver workflow.

### Step 3:
Implementation using Python code.

### Step 4:
Import the necessary modules.

### Step 5:
Define a custom request handler.

### Step 6:
Start an HTTP server on a specific port.

### Step 7:
Run the Python script to serve web pages.

### Step 8:
Serve the HTML pages.

### Step 9:
Start the server script and check for errors.

### Step 10:
Open a browser and navigate to http://127.0.0.1:8000 (or the assigned port).

## PROGRAM:
```
from http.server import HTTPServer, BaseHTTPRequestHandler

content = """
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Lenovo ThinkPad E16 Specifications</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #f4f4f4;
            margin: 0;
            padding: 0;
        }
        header {
            background-color: #333;
            color: white;
            padding: 10px 0;
            text-align: center;
        }
        .container {
            width: 80%;
            margin: 20px auto;
            background-color: white;
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
            padding: 20px;
        }
        h1 {
            color: #333;
        }
        table {
            width: 100%;
            border-collapse: collapse;
            margin-top: 20px;
        }
        table, th, td {
            border: 1px solid #ddd;
        }
        th, td {
            padding: 12px;
            text-align: left;
        }
        th {
            background-color: #f1f1f1;
        }
        td {
            background-color: #fafafa;
        }
        .footer {
            background-color: #333;
            color: white;
            padding: 10px 0;
            text-align: center;
            position: fixed;
            width: 100%;
            bottom: 0;
        }
        /* General Reset */
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}

/* Body Styling */
body {
    font-family: Arial, sans-serif;
    background-color: #f4f4f4;
    margin: 0;
    padding: 0;
}

/* Header Styling */
header {
    background-color: #333;
    color: white;
    padding: 20px 0;
    text-align: center;
}

/* Main Container */
.container {
    width: 80%;
    margin: 20px auto;
    background-color: white;
    box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
    padding: 20px;
}

/* Title Styling */
h1 {
    font-size: 2.5em;
    color: #fff;
}

h2 {
    font-size: 1.8em;
    color: #333;
    margin-bottom: 20px;
}

/* Table Styling */
table {
    width: 100%;
    border-collapse: collapse;
    margin-top: 20px;
}

th, td {
    padding: 12px;
    text-align: left;
    border: 1px solid #ddd;
}

/* Table Header Styling */
th {
    background-color: #f1f1f1;
    color: #333;
    font-weight: bold;
}

/* Table Data Row Styling */
td {
    background-color: #fafafa;
    color: #555;
}

/* Footer Styling */
.footer {
    background-color: #333;
    color: white;
    padding: 10px 0;
    text-align: center;
    position: fixed;
    width: 100%;
    bottom: 0;
}

/* Responsive Design */
@media (max-width: 768px) {
    .container {
        width: 90%;
    }

    th, td {
        font-size: 14px;
        padding: 8px;
    }

    h1 {
        font-size: 2em;
    }

    h2 {
        font-size: 1.6em;
    }
}

    </style>
</head>
<body>

<header>
    <h1  style="color: aqua;">Lenovo ThinkPad E16 Specifications</h1>
</header>

<div class="container">
    <h2 style="color: blue;">Key Specifications</h2>
    <table>
        <tr>
            <th style="color: burlywood;">Specification</th>
            <th style="color: blue;">Details</th>
        </tr>
        <tr>
            <td style="color: burlywood;">Model</td>
            <td style="color: blue;">Lenovo ThinkPad E16</td>
        </tr>
        <tr>
            <td style="color: burlywood;">Processor</td>
            <td style="color: blue;">Intel Core i5 or i7 (12th Gen)</td>
        </tr>
        <tr>
            <td style="color: burlywood;">Display</td>
            <td style="color: blue;">16.0" Full HD (1920 x 1200) IPS</td>
        </tr>
        <tr>
            <td style="color: burlywood;">Graphics</td>
            <td style="color: blue;">Intel Iris Xe Graphics</td>
        </tr>
        <tr>
            <td style="color: burlywood;">RAM</td>
            <td style="color: blue;">8GB / 16GB DDR4</td>
        </tr>
        <tr>
            <td><style="color: burlywood;">Storage</td>
            <td style="color: blue;">256GB / 512GB SSD</td>
        </tr>
        <tr>
            <td style="color: burlywood;">Battery</td>
            <td style="color: blue;">45Wh, up to 10 hours</td>
        </tr>
        <tr>
            <td style="color: burlywood;">Operating System</td>
            <td style="color: blue;">Windows 11 Pro</td>
        </tr>
        <tr>
            <td style="color: burlywood;" >Ports</td>
            <td style="color: blue;">2 x USB-A 3.2, 2 x USB-C 3.2, HDMI 2.0, RJ45 Ethernet, Audio Jack</td>
        </tr>
        <tr>
            <td style="color: burlywood;">Weight</td>
            <td style="color: blue;">1.70 kg (3.75 lbs)</td>
        </tr>
        <tr>
            <td style="color: burlywood;">Keyboard</td>
            <td style="color: blue;">Backlit Keyboard</td>
        </tr>
        <tr>
            <td style="color: burlywood;">Camera</td>
            <td style="color: blue;">720p HD Webcam</td>
        </tr>
        <tr>
            <td style="color: burlywood;">Color</td>
            <td style="color: blue;">Black</td>
        </tr>
    </table>
</div>

<div class="footer">
    <p>&copy; 2024 Lenovo. All Rights Reserved.</p>
</div>

</body>
</html>
"""

class myhandler(BaseHTTPRequestHandler):
    def do_GET(self):
        print("request received")
        self.send_response(200)
        self.send_header('content-type', 'text/html; charset=utf-8')
        self.end_headers()
        self.wfile.write(content.encode())

server_address = ('', 8000)
httpd = HTTPServer(server_address, myhandler)
print("my webserver is running...")
httpd.serve_forever()
```
## OUTPUT:


![Screenshot 2025-05-07 110123](https://github.com/user-attachments/assets/0e9d1cac-2ae6-4acf-92aa-e25b70bc0708)

## RESULT:
The program for implementing simple webserver is executed successfully.
