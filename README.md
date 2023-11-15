# Ex.05 Design a Website for Server Side Processing
## Register Number : 212221040082
## Date: 15-11-2023

## AIM:
To design a website to find total surface area of a square prism in server side. 

## FORMULA:
Total Surface Area = 2b<sup>2</sup> + 4bh
<br>b --> Base of Square Prism
<br>h --> Height of Square Prism

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

## PROGRAM :

### math.html:
```
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset='utf-8'>
    <meta http-equiv='X-UA-Compatible' content='IE=edge'>
    <title>Area of Rectangle</title>
    <meta name='viewport' content='width=device-width, initial-scale=1'>
    <style type="text/css">
      body 
      {
      background-color:white;
      overflow-x: hidden;
      }
      .edge {
      width: 1640px;
      margin-left: auto;
      margin-right: auto;
      padding-top: 250px;
      padding-left: 300px;
      }
      .box {
      display:block;
      width: 500px;
      height: 400px;
      font-size: 30px;
      margin-right: auto;
      margin-top: -130px;
      margin-left: 200px;
      background-color:#190019;
      box-shadow:20px 40px 40px rgba(0, 0, 0, .5);
      }
      .formelt{
      color:#eaac8b;
      text-align: center;
      margin-top: 7px;
      margin-bottom: 6px;
      }
      input[type=text]{
          width: 50px;
          height: 35px;
          font-size: 25px;
          color: white;
          background-color: transparent;
          border: none;
          text-align: end;
      }
      input[type=submit]{
          height: 40px;
          font-size: 25px;
          font-weight: bolder;
          background-color:#f92e57;
          color: black;
          border: none;
          margin-top: 10px;
      }
      h1
      {
      color:#f92e57;
      text-align: center;
      padding-top: 20px;
      }
    </style>
  </head>
  <body>
    <div class="edge">
      <div class="box">
        <h1>Area of a Rectangle</h1>
          <form method="POST">
            {% csrf_token %}
            <div class="formelt">
              <b> &nbsp;&nbsp;   Base : </b><input type="text" name="length" value="{{b}}"> </input>(in m)<br/>
            </div>
            <div class="formelt">
              <b>Height : </b><input type="text" name="breadth" value="{{h}}"> </input>(in m)<br/>
            </div>
            <div class="formelt">
              <input type="submit" value="Calculate"></input><br/>
            </div>
            <div class="formelt">
              <b>Surface Area : </b><input type="text" name="area" value="{{area}} "> </input>m<sup>2</sup><br/>
            </div>
          </form>
      </div>
    </div>
  </body>
</html>
```
## SERVER SIDE PROCESSING:

### urls.py:
```
"""
URL configuration for sample project.

The `urlpatterns` list routes URLs to views. For more information please see:
    https://docs.djangoproject.com/en/4.2/topics/http/urls/
Examples:
Function views
    1. Add an import:  from my_app import views
    2. Add a URL to urlpatterns:  path('', views.home, name='home')
Class-based views
    1. Add an import:  from other_app.views import Home
    2. Add a URL to urlpatterns:  path('', Home.as_view(), name='home')
Including another URLconf
    1. Import the include() function: from django.urls import include, path
    2. Add a URL to urlpatterns:  path('blog/', include('blog.urls'))
"""
from django.contrib import admin
from django.urls import path
from myapp import views
urlpatterns = [
    path('admin/', admin.site.urls),
    path('areaofrectangle/',views.rectarea,name="areaofrectangle"),
    path('',views.rectarea,name="areaofrectangleroot")
]

```

### views.py:
```
from django.shortcuts import render

def rectarea(request):
    context = {}
    context['area'] = "0"
    context['b'] = "0"
    context['h'] = "0"

    if request.method == 'POST':
        print("POST method is used")
        h = request.POST.get('length', '0')
        b = request.POST.get('breadth', '0')
        print('request=', request)
        print('Base=', b)
        print('height=', h)
        area = (2 * int(h) * int(h)) + (4 * int(b) * int(h))
        context['area'] = area
        context['h'] = h
        context['b'] = b
        print('Surface Area=', area)

    return render(request, 'myapp/math.html', context)

```

## HOMEPAGE:

![image](https://github.com/keerthysesha/MathServer/assets/125575936/f0d70c24-94d7-4e05-b05a-77c9f6f96d33)


## RESULT:
The program for performing server side processing is completed successfully.
