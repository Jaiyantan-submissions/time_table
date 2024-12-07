# Ex03 Time Table
# Date:
# AIM
To write a html webpage page to display your slot timetable.

# ALGORITHM
## STEP 1
Create a Django-admin Interface.

## STEP 2
Create a static folder and inert HTML code.

## STEP 3
Create a simple table using `<table>` tag in html.

## STEP 4
Add header row using `<th>` tag.

## STEP 5
Add timetable using `<td>` tag.

## STEP 6
Execute the program using runserver command.

# PROGRAM :

# views.py:

    from django.shortcuts import render

    def timetable(request):
        return render(request, 'timetable.html')

    def subject_details(request):
    
        subjects = [
            {"name": "CE", "overview": "Communicative English. \n Includes basic grammar vocabulary required for professional english communication", "teacher": "DR. Subashini"},
            {"name": "BEEE", "overview": "Basic Electrical and Electronics Engineering. \n Includes Fundamentals of Electrical Engineering", "teacher": "DR. Muthuvel"},
            {"name": "Python", "overview": "Programming with Python. \n Includes Python syntax, frameworks and logic building", "teacher": "DR. Ulagammai"},
            {"name": "Linear Algebra", "overview": "Foundations of Linear Algebra. \n Includes Mathematics required to understand Machine Learning models", "teacher": "DR. Ulagammai"},
            {"name": "WEB", "overview": "Web Development Technologies.\n Includes networking and the know hows of the underlying Web Architecture", "teacher": "Ms. Berlin"},
        ]
        return render(request, 'subject_details.html', {'subjects': subjects})

# timetable.html:

    {% load static %}
    <!DOCTYPE html>
    <html lang="en">
    <head>
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <title>Timetable</title>
        <style>
            /* High-tech background gradient */
            body {
                font-family: Arial, sans-serif;
                margin: 0;
                padding: 0;
                background: linear-gradient(135deg, #1e293b, #0f172a);
                color: white;
                min-height: 100vh;
                overflow-x: hidden;
            }

            header {
                display: flex;
                align-items: center;
                margin: 20px;
            }

            header img {
                width: 80px;
                height: 80px;
                margin-right: 10px;
            }

            header h1 {
                font-size: 24px;
                margin: 0;
            }

            .container {
                background: rgba(255, 255, 255, 0.1);
                backdrop-filter: blur(10px);
                border-radius: 10px;
                box-shadow: 0 8px 20px rgba(0, 0, 0, 0.5);
                padding: 20px;
                margin: 20px auto;
                max-width: 900px;
            }

            table {
                width: 100%;
                border-collapse: collapse;
                margin: 20px 0;
            }

            th, td {
                border: 1px solid rgba(255, 255, 255, 0.3);
                padding: 10px;
                text-align: center;
            }

            th {
                background-color: #2563eb;
                color: white;
            }

            td {
                font-size: 16px;
                color: #e2e8f0;
            }

            tr:nth-child(even) {
                background-color: rgba(255, 255, 255, 0.05);
            }

            .scrollable {
                max-height: 75vh;
                overflow-y: auto;
            }

            .button-container {
                text-align: center;
                margin-top: 20px;
            }

            .view-details-btn {
                background-color: #1e88e5;
                color: white;
                padding: 10px 20px;
                font-size: 16px;
                text-transform: uppercase;
                border: none;
                border-radius: 5px;
                cursor: pointer;
                transition: background-color 0.3s ease;
                text-decoration: none;
            }

            .view-details-btn:hover {
                background-color: #0d47a1;
            }
        </style>
    </head>
    <body>
        <header>
            <img src="{% static 'images/logo.jpeg' %}" alt="SAVEETHA ENGINEERING COLLEGE LOGO"/>
            <h1>SAVEETHA SCOFT ODD JUNIOR Timetable</h1>
        </header>
        <div class="container">
            <div class="scrollable">
                <table>
                    <caption>JAIYANTAN S</caption>
                    <thead>
                        <tr>
                            <th>Day</th>
                            <th>8:00 - 10:00</th>
                            <th>10:00 - 12:00</th>
                            <th>1:00 - 3:00</th>
                            <th>3:00 - 5:00</th>
                        </tr>
                    </thead>
                    <tbody>
                        <tr>
                            <td>Monday</td>
                            <td></td>
                            <td>CE (4P1-2)</td>
                            <td>WEB (6LI-1)</td>
                            <td></td>
                        </tr>
                        <tr>
                            <td>Tuesday</td>
                            <td>BEEE (2L3B-2)</td>
                            <td></td>
                            <td>Linear Algebra (19AI301C)</td>
                            <td></td>
                        </tr>
                        <tr>
                            <td>Wednesday</td>
                            <td></td>
                            <td>BEEE</td>
                            <td>ECAM SCOFT(MENTOR)</td>
                            <td></td>
                        </tr>
                        <tr>
                            <td>Thursday</td>
                            <td>CE (4P1-2)</td>
                            <td>Python (19AI301C)</td>
                            <td>CDS (19EY308)</td>
                            <td></td>
                        </tr>
                        <tr>
                            <td>Friday</td>
                            <td></td>
                            <td>WEB (6LI-1)</td>
                            <td>Linear Algebra (19AI301C)</td>
                            <td></td>
                        </tr>
                        <tr>
                            <td>Saturday</td>
                            <td></td>
                            <td>WEB (6LI-1)</td>
                            <td>Python (19AI301C)</td>
                            <td></td>
                        </tr>
                    </tbody>
                </table>
            </div>
            <div class="button-container">
                <a href="{% url 'subject_details' %}" class="view-details-btn">View More Details</a>
            </div>
        </div>
    </body>
    </html>

# details.html:

    <!DOCTYPE html>
    <html lang="en">
    <head>
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <title>Subject Details</title>
        <style>
            body {
                font-family: Arial, sans-serif;
                margin: 0;
                padding: 20px;
                background: linear-gradient(135deg, #0f172a, #1e293b);
                color: white;
            }

            .container {
                max-width: 800px;
                margin: auto;
                padding: 20px;
                background: rgba(255, 255, 255, 0.1);
                border-radius: 10px;
            }

        
            .button-container {
                text-align: center;
                margin-top: 20px;
            }
            
            .view-details-btn {
                background-color: #1e88e5;
                color: white;
                padding: 10px 20px;
                font-size: 16px;
                text-transform: uppercase;
                border: none;
                border-radius: 5px;
                cursor: pointer;
                transition: background-color 0.3s ease;
                text-decoration: none;
            }
            
            .view-details-btn:hover {
                background-color: #0d47a1;
            }
            h1 {
                text-align: center;
                color: #60a5fa;
            }

            .subject {
                margin: 20px 0;
                padding: 10px;
                background: rgba(255, 255, 255, 0.1);
                border: 1px solid rgba(255, 255, 255, 0.3);
                border-radius: 5px;
            }
            .subject:hover{
                background: rgba(255, 255, 255, 0.226);
            }

            .subject h2 {
                margin: 0;
                color: #93c5fd;
            }

            .subject p {
                margin: 5px 0;
            }
        </style>
    </head>
    <body>
        <div class="container">
            <h1>Subject Details</h1>
            {% for subject in subjects %}
            <div class="subject">
                <h2>{{ subject.name }}</h2>
                <p><strong>Overview:</strong> {{ subject.overview }}</p>
                <p><strong>Teacher:</strong> {{ subject.teacher }}</p>
            </div>
            {% endfor %}
        </div>
        <div class="button-container">
            
                <a href="{% url 'timetable' %}" class="view-details-btn">Back to TimeTable</a>
            
            
        </div>
    </body>
    </html>


# OUTPUT:

!['Result pic](output1.png)
!['result pic](output2.png)
# RESULT
The program for creating slot timetable using basic HTML tags is executed successfully.
