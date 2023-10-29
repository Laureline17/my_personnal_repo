# Project work 1


I choose the following task :
"As an UNDAC Deputy Team Leader I want to maintain a list of team members so that I can contact them immediately"

My task is to create a feature in the UNDAC application that will make it possible to maintain a list of team members
so that they can be contacted immediately. 
This list should therefore contain essential contact information for each member of the team.
To make it more usefull, my task is also to make some filters and a way to search people inside the list by their skills or 
their current assignement. 

I tried to organize my code to make it clear for my teamates and to make my code more efficient. 
With the group we aggree to make two folder. One called "Medels" where I could put my class. And the other one called View. 
First I create a class in Models called "TeamMemberModels". In this class, I put all the things that we need to describe one 
team members. For example, their name, their skill, thier current assignement...

```
namespace UNDAC_Project.Models
{
    public class TeamMemberModels
    {
        public string Name { get; set; }
        public string Skill { get; set; }
        public string CurrentAssignment { get; set; }
        public string ContactInformation { get; set; }
    }
}
```
I made it public so the other members of my team can also use it. This simplifies the code and avoids repetition.

After, in the folder View I created "TeamMembersPage.xaml.cs".In this folder, I was able to code all the functions I needed 
to my task to work.
In particular, I create three function. One to search by skills, one to search by current assignement and one to make a search toolbar.

```
        private void FilterBySkill(object sender, EventArgs e)
        {
            string selectedSkill = skillComboBox.SelectedItem as string;

            if (!string.IsNullOrEmpty(selectedSkill))
            {
                var filteredMembers = TeamMembers.Where(member =>
                    member.Skill.Equals(selectedSkill, StringComparison.OrdinalIgnoreCase)
                ).ToList();

                teamMembersListView.ItemsSource = filteredMembers;
            }
            else
            {
                teamMembersListView.ItemsSource = TeamMembers;
            }
        }
```

This is an example of how I made my functions. This one is to search a member by his skills. 
Of course, before these functions, I created a list of skills and one list of current assignement. 

To make my page accessible, I creat a button on the main page. 

```
        private async void GoToTeamMemberListPage(object sender, EventArgs e)
        {
            await Navigation.PushAsync(new TeamMembersPage());
        }
```

This is the code of my button. But it will not be the final version because we haven't decide yet the design of our page. 


## My teamate's code review

https://github.com/timh1975/UNDAC-Project/pull/47

SearchTeamMembers, FilterBySkill and FilterByAssignment
```
        private void SearchTeamMembers(object sender, TextChangedEventArgs e)
        {
            string searchKeyword = e.NewTextValue.ToLower();

            if (!string.IsNullOrEmpty(searchKeyword))
            {
                var filteredMembers = TeamMembers.Where(member =>
                    member.Name.ToLower().Contains(searchKeyword) ||
                    member.Skill.ToLower().Contains(searchKeyword) ||
                    member.CurrentAssignment.ToLower().Contains(searchKeyword)
                ).ToList();

                teamMembersListView.ItemsSource = filteredMembers;
            }
            else
            {
                teamMembersListView.ItemsSource = TeamMembers;
            }
        }

        private void FilterBySkill(object sender, EventArgs e)
        {
            string selectedSkill = skillComboBox.SelectedItem as string;

            if (!string.IsNullOrEmpty(selectedSkill))
            {
                var filteredMembers = TeamMembers.Where(member =>
                    member.Skill.Equals(selectedSkill, StringComparison.OrdinalIgnoreCase)
                ).ToList();

                teamMembersListView.ItemsSource = filteredMembers;
            }
            else
            {
                teamMembersListView.ItemsSource = TeamMembers;
            }
        }

        private void FilterByAssignment(object sender, EventArgs e)
        {
            string selectedAssignment = assignmentComboBox.SelectedItem as string;

            if (!string.IsNullOrEmpty(selectedAssignment))
            {
                var filteredMembers = TeamMembers.Where(member =>
                    member.CurrentAssignment.Equals(selectedAssignment, StringComparison.OrdinalIgnoreCase)
                ).ToList();

                teamMembersListView.ItemsSource = filteredMembers;
            }
            else
            {
                teamMembersListView.ItemsSource = TeamMembers;
            }
        }
 ```
These three functions look and serve the same purpose,
returning the same information and often taking the same/similar inputs. 
I would consider refectoring into either one single function to "filter", then have varyign functions call on this filter 
to reduce repetition within your code. Alternatively, one function that then recieves a variabel to determine the type of 
search it needs to undertake.

## My fixes

```
private void FilterTeamMembers(object sender, EventArgs e)
        {
            string searchKeyword = searchEntry.Text.ToLower();
            string selectedSkill = skillComboBox.SelectedItem as string;
            string selectedAssignment = assignmentComboBox.SelectedItem as string;

            var filteredMembers = TeamMembers;

            if (!string.IsNullOrEmpty(searchKeyword))
            {
                filteredMembers = filteredMembers.Where(member =>
                    member.Name.ToLower().Contains(searchKeyword) ||
                    member.Skill.ToLower().Contains(searchKeyword) ||
                    member.CurrentAssignment.ToLower().Contains(searchKeyword)
                ).ToList();
            }

            if (!string.IsNullOrEmpty(selectedSkill))
            {
                filteredMembers = filteredMembers.Where(member =>
                    member.Skill.Equals(selectedSkill, StringComparison.OrdinalIgnoreCase)
                ).ToList();
            }

            if (!string.IsNullOrEmpty(selectedAssignment))
            {
                filteredMembers = filteredMembers.Where(member =>
                    member.CurrentAssignment.Equals(selectedAssignment, StringComparison.OrdinalIgnoreCase)
                ).ToList();
            }

            teamMembersListView.ItemsSource = filteredMembers;
        }
```

To reduce my code and to match my teamate's review code I've combined the three functions into one.

## My code review of my teamate's code
First, the structure of the code is good and readable, the variables name are correct and understandable.
Just, to make things easier to understand it will be better to add more coments.
Maybe, in Models/Alerts.cs the properties of the class are defined as private with private set accessors. 
This means that these properties can only be defined inside the Alert class. However, it is possible that we also want a 
way of accessing and modifying these properties outside the class, in which case the accessors should be public or at least 
internal.
Otherwise the code is clear and well structured and there is no duplication of code.

## General reflection

https://github.com/timh1975/UNDAC-Project/pull/45

This week I understand why it is really important to communicate and the importance of github when we worked in team.
In fact, this week I saw that one snippets of a code that I did, could be also used by someone else. 
In a team development situation it could happen that there is confilcts between two code and before merging it's important 
to solve those conflicts. 
Otherwise, the all project can't run.


