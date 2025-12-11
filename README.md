# Ex.04 Design a Website for Server Side Processing
## Date: 11-12-2025

## AIM:
To create a web page to calculate vehicle mileage and fuel efficiency using server-side scripts.

## FORMULA:
M = D / F
<br> M --> Mileage (in km/l)
<br> D --> Distance Travelled (in km)
<br> F --> Fuel Consumed (in l)

## DESIGN STEPS:

### Step 1:
Clone the repository from GitHub.

### Step 2:
Create Django Admin project.

### Step 3:
Create a New App under the Django Admin project.

### Step 4:
Create python programs for views and urls to perform server side processing.

### Step 5:
Create a HTML file to implement form based input and output.

### Step 6:
Publish the website in the given URL.

## PROGRAM:
```
math.html
<html>
<head>
    <title>Mileage Calculator</title>
    <style>
        body 
        {
            background: linear-gradient(lightyellow, green);
        }
        
        .box 
        {
            text-align: center;
            size: 10px;
            width: 90%;
            background: linear-gradient(#16bffd, #cb3066);
            border: groove 4px rgb(255, 47, 0);
            padding: 20px;
            margin: 40px auto;
        }
        .result 
        {
            font-weight: bold;
        }
    </style>
</head>
<body>

    <div class="box">
       <h3> Mileage Calculation</h3> 
        <h5>S.Manigandan (25004934)</h5>

        <form method="post">
            {% csrf_token %}
            <label>Distance</label>
            <br>
            <input type="number" name="distance"> (km)
            <br>
            <br>
            <label>Fuel consumed</label>
            <br>
            <input type="number" name="liters"> (L)
            <br>
            <br>
            <button type="submit">Calculate</button>
            <br>
            <br>
            <label>Mileage</label>
            <br>
            <input class='result' type="number" name="Mileage" value={{miles}}>(Km/L)
        </form>
    </div>
</body>
</html>

views.py
from django.shortcuts import render
def fmiles(request):
    km = int(request.POST.get('distance', 0))
    l = int(request.POST.get('liters', 0))
    miles = km / l if request.method == 'POST' and l != 0 else 0
    print("kilometers =", km)
    print("liters =", l)
    print("Mileage =", miles)
    return render(request, 'mathapp/math.html', {'km': km, 'l': l, 'miles': miles})

urls.py
from django.urls import path
from mathapp import views

urlpatterns = [
    path('', views.fmiles, name='fmiles'),
]

```

## OUTPUT - SERVER SIDE:
![alt text](<Screenshot (70).png>)

## OUTPUT - WEBPAGE:
![alt text](<Screenshot (69).png>)

## RESULT:
The a web page to calculate vehicle mileage and fuel efficiency using server-side scripts is created successfully.
