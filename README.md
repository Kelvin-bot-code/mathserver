# Ex.05 Design a Website for Server Side Processing
# Date: 7.12.2024
# AIM:
To design a website to calculate the power of a lamp filament in an incandescent bulb in the server side.

# FORMULA:
P = I^2 R
P --> Power (in watts)
 I --> Intensity
 R --> Resistance

# DESIGN STEPS:
## Step 1:
Clone the repository from GitHub.

## Step 2:
Create Django Admin project.

## Step 3:
Create a New App under the Django Admin project.

## Step 4:
Create python programs for views and urls to perform server side processing.

## Step 5:
Create a HTML file to implement form based input and output.

## Step 6:
Publish the website in the given URL.

# PROGRAM :
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Lamp Power Calculator</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #f4f4f9;
            color: #333;
            margin: 0;
            padding: 20px;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
        }

        h1 {
            color: #2c3e50;
        }

        label {
            font-weight: bold;
            display: block;
            margin-top: 10px;
        }

        input[type="number"] {
            width: 100%;
            padding: 8px;
            margin-top: 5px;
            margin-bottom: 15px;
            border: 1px solid #ccc;
            border-radius: 5px;
            font-size: 16px;
        }

        button {
            background-color: #3498db;
            color: #fff;
            border: none;
            padding: 10px 15px;
            border-radius: 5px;
            font-size: 16px;
            cursor: pointer;
        }

        button:hover {
            background-color: #2980b9;
        }

        #result {
            margin-top: 20px;
            font-size: 18px;
            color: #27ae60;
            font-weight: bold;
        }

        .container {
            background: #fff;
            padding: 30px;
            border-radius: 10px;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
            max-width: 400px;
            width: 100%;
        }
    </style>
    <script>
        function calculatePower() {
            var I = parseFloat(document.getElementById("current").value);
            var R = parseFloat(document.getElementById("resistance").value);
            if (isNaN(I) || isNaN(R)) {
                document.getElementById("result").innerHTML = "Please enter valid numbers for current and resistance.";
                return;
            }
            var P = Math.pow(I, 2) * R;
            document.getElementById("result").innerHTML = "Power (P) = " + P.toFixed(4) + " Watts";
        }
    </script>
</head>
<body>
    <div class="container">
        <h1>Lamp Power Calculator</h1>
        <label for="current">Current (I) in Amps:</label>
        <input type="number" id="current" step="any">
        <label for="resistance">Resistance (R) in Ohms:</label>
        <input type="number" id="resistance" step="any">
        <button onclick="calculatePower()">Calculate Power</button>
        <div id="result"></div>
    </div>
</body>
</html>
```
# views.py
```html

from django.shortcuts import render 
def lampspower(request): 
    context={} 
    context['power'] = "0" 
    context['i'] = "0" 
    context['r'] = "0" 
    if request.method == 'POST': 
        print("POST method is used")
        i = request.POST.get('I','0')
        r = request.POST.get('R','0')
        print('request=',request) 
        print('Intensity=',i) 
        print('Resistance=',r) 
        power = (int(i)*int(i))*int(r) 
        context['power'] = power 
        context['i'] = i
        context['r'] = r 
        print('Power=',power) 
    return render(request,'myapp/calc.html',context)
```
# urls.py
```html

from django.contrib import admin
from django.urls import path
from mathapp import views

urlpatterns = [
    path('admin/', admin.site.urls),
    path('lampspower/',views.lampspower,name="lampspower"),
    path('',views.lampspower,name="lampspower")
]
```
# SERVER SIDE PROCESSING:
![Screenshot 2024-12-06 210338](https://github.com/user-attachments/assets/f260c2c8-1988-402a-ad1f-617b9573d3e7)


# HOMEPAGE:
![Screenshot 2024-12-06 210031](https://github.com/user-attachments/assets/bcdadcac-62c2-4b30-acd6-d4fa9b5e184c)


# RESULT:
The program for performing server side processing is completed successfully.
