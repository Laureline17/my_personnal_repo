# Project work 2

## Summary of my task

For this week I have chosen the following task : 
As an UNDAC Team Leader I want to view security alerts so that I can inform appropriate partners. 

This task involves displaying alert notifications and managing them. It is a very usefull task on the project because all the important information
could not be view by anyone without this task. 


## Snippets from my code

For this task, I choose to follow the same structure as I did last week to make it easier for my teamates to understand my code. 
So I create a new branch and I made two new folders. One named "Models" and one named "View".

In the folders "Models" I create a new class "Alert". This is what is inside my folders Models.

```
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace UNDAC_Project.Models
{
    public class Alert
    {
        public int Id { get; private set; }
        public string Message { get; private set; }
        public DateTime CreatedAt { get; private set; }
        public bool IsResolved { get; set; }

        public Alert(int id, string message, DateTime createdAt)
        {
            Id = id;
            Message = message;
            CreatedAt = createdAt;
            IsResolved = false;
        }
    }
}
```

I made my class public so everyone on my team can use it if they need to.

On the folders View I add one contentPage so I have one .xaml and one .xaml.cs 

```
namespace UNDAC_Project.Views
{
    public partial class AlertListView : ContentPage
    {
        public AlertListView()
        {
            InitializeComponent();

            var alerts = new List<Alert>
            {
                new Alert(1, "Security issue 1", DateTime.Now),
                new Alert(2, "Security issue 2", DateTime.Now),
            };

            alertList.ItemsSource = alerts;
        }
    }
}
```
I created a list with my alerts so I can display them. To make my page accessible, I created a button on the main page that acces to my own page.

## Code review of my code
Alert.cs:
The class is well structured, simple and follows good class design practice. 
The properties of the class correspond to the information relating to security alerts.

AlertListView.xaml:
The XAML structure is correct and displays a list of security alerts. 
The use of a ListView allows the alerts to be displayed in a scrolling list, and the alerts are displayed correctly.
Finally, the binding between the Model and the View is correctly configured.

AlertListView.xaml.cs:
The AlertListView class correctly uses the list of alerts to populate ListView. 
The user interface is appropriate for what is required.

However, the current class does not take into account all the criteria of the task,
i.e. it lacks the immediate display of alerts as soon as they are created, as well as the visual and audio accompaniment and management 
of the alert history. These features need to be added.


I tried to respond to all the criteria but I had somme dificulties so I choose to join the blue team. And I will continue to search solutions
to make my code to answer all the criteria. But for this I choose to let my code like that so it can compile and not to prevent my teamates to
test their codes. 


## Code review of my teamate's code

To begin with, this code is very well organised. It's split into two different files (Models and View), which is handy for re-reading the code.
You might consider moving the creation of the dummy resource list to a separate class or service to make the code more modular and easier to test.

## General reflective section

This week I had a problem with my visual studio. I haven't foun the problem yet so I had to ask one of my teamate to push my branch with my code 
this week. I think something has been de-allocated by mistake so I will have to find the problem and to solve it.

I tried to not do the same mistakes as last week in my code.
So I tried to make it more simple and to not repeat myself. 
It was easier to make this week. 

This week I understand the importance to only add codes that compile on the project. If not, the projet entierly will not compilke and it will
affect the whole group. 



