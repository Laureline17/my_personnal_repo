# Requirements specification

## Summary of my task 

This week I choose the following task : 
"As a system administrator, I want to maintain reference values for roles"
This task involves managing the different role values.
To complete this task I have to be able to add, update and delete references values for role. 

## Our organisation
In order to organise our new project properly, we have put in place rules that every member of the team must respect.
This organisation will help us to work better as a team and avoid any conflicts in the code. 
So we've agreed on these rules, which a friend has written in the documentation section of our github.
First we agrred that everybody need to create their own branch to work on their issues.
ANd before merging our branch to the branch dev we have to make sure that the code review has been made.

## Snippets from my code
So I created my branch "feature#18" and I cretae two new folders. One named Models to put my class in. And an other one named Views. 

In order to interact with the database, it is important not to forget the following line of code:
```
using SQLite;
```

```
namespace UndacBlue.Models
{
    [Table("Role")]
    public class Role
    {
        [PrimaryKey, AutoIncrement, Column("_id")]
        public int Id { get; set; }

        public string Name { get; set; }

    }
}
```
Here my primary key for the table is the Id property, which must be auto-incrementing, and in the database it will be represented by a column called "_id".
And name is a string property which represents the name of the role in the database.

In my task I have to be able to interact with those roles, I have to be able to add some role, to delete them or to update them.


```
        private void BtnCreate_Click(object sender, EventArgs e)
        {
            string roleName = txtRoleName.Text;
            if (!string.IsNullOrEmpty(roleName))
            {
                Role newRole = new Role { Name = roleName };
                roleModel.AddRole(newRole);
                LoadRoles();
                ClearTextBox();
            }
        }

        private void BtnUpdate_Click(object sender, EventArgs e)
        {
            string Name = txtRoleName.Text;
            if (!string.IsNullOrEmpty(Name) && lstRoles.SelectedItem != null)
            {
                roleModel.UpdateRole((Role)lstRoles.SelectedItem, Name);
                LoadRoles();
                ClearTextBox();
            }
        }

        private void BtnDelete_Click(object sender, EventArgs e)
        {
            if (lstRoles.SelectedItem != null)
            {
                roleModel.DeleteRole((Role)lstRoles.SelectedItem);
                LoadRoles();
                ClearTextBox();
            }
        }
```

Here is the code I use to manipulate my roles.  
The BtnCreate_Click retrieves the role name from the txtRoleName text field. 
If the name is not empty, it creates a new Role object with this name.
It then adds the new role to the list of roles via the AddRole method of the roleModel object.
Refreshes the view by reloading the roles and deleting the text field.

The BtnUpdate_Click works in much the same way.
It retrieves the new role name from the txtRoleName text field.
If the new name is not empty and a role is selected in the list, updates the selected role with the new name via the UpdateRole method of the roleModel object.
Refreshes the view by reloading the roles and clearing the text field.

Finally, the BtnDelete_Click works quite simply and similarly to the two previous buttons.
If a role is selected in the list, it deletes the selected role via the DeleteRole method of the roleModel object.
And refreshes the view by reloading the roles and deleting the text field

## Code review of my code

Everything looks good to me, some things could be changed though.

Try make sure all comments are in English, I know it's not a ton but having some of other languages will make it confusing.
For your model, have it inherit from INotifyPropertyChanged and invoke property change events when they happen.

## Problems encountered

This week I was enable to solve all of my errors. 
![screenshot 1](images/Erreur.png)
<figcaption><b>Fig.1.1 - My error </b></figcaption><br><br>

I tried differents things to solve it but I could find the solution.
According to what I've been told, the vela error is a format conversion problem.
But I've tried different ways to get the format to match but unfortunately I haven't managed to solve my problem.

## What I learned this week

This week I understand the importance of the respect for the deadline. 
With our team we had agreed to finish the code on Friday so that we would have time to do the code review properly.
But unfortunately my teamate didn't respect this deadline so I couldn't do his code review because I didn't have it.
This is very common in group work, especially in large groups. So it is very important to learn to deal with it. 
And more important, to try to don't do it. 
So I will see with him if he had problem to do his task and I will try to help him. 

