# Implementation

## My issue
This week I xorked on the following issue : "As an UNDAC Deputy Team Leader I want to view details of all team partners so that I can contact them 
immediately"
The aim of this issue was to list all of the team member with their informations present on the database to make the contact with them possible. 

## Snippets from my code

For this week I had to change the database.c because I needed the database. So I make some update to make the access of my table possible.

```
    public Task<List<PartnerAgency>> GetPartnerAgenciesAsync()
        {
            return _database.Table<PartnerAgency>().ToListAsync();
        }

        public Task<PartnerAgency> GetPartnerAgencyAsync(int id)
        {
            return _database.Table<PartnerAgency>().Where(i => i.Id == id).FirstOrDefaultAsync();
        }

        public Task<int> SavePartnerAgencyAsync(PartnerAgency partnerAgency)
        {
            if (partnerAgency.Id != 0)
            {
                return _database.UpdateAsync(partnerAgency);
            }
            else
            {
                return _database.InsertAsync(partnerAgency);
            }
        }

        public Task<int> DeletePartnerAgencyAsync(PartnerAgency partnerAgency)
        {
            return _database.DeleteAsync(partnerAgency);
        }
    }
```

GetPartnerAgency retrieves a list of all the Partners Agency objects of the database. 
These methods encapsulate the basic CRUD (Create, Read, Update, Delete) operations for managing PartnerAgency objects in the SQLite database. 

Next I created two news folders called "Models" and "Views", because with my team we decided to keep this method to organise our code because it's working. 

```
 private void InitializePartnerAgencies()
        {
            var partnerAgencies = _database.GetPartnerAgenciesAsync().Result;

            if (partnerAgencies == null || partnerAgencies.Count == 0)
            {
                partnerAgencies = new List<PartnerAgency>
                {
                    new PartnerAgency { Name = "Agency 1", AssociationStatus = "Requested", ContactPerson = "Contact 1", ContactEmail = "contact1@example.com" },
                    new PartnerAgency { Name = "Agency 2", AssociationStatus = "Confirmed", ContactPerson = "Contact 2", ContactEmail = "contact2@example.com" },
                };

                foreach (var partnerAgency in partnerAgencies)
                {
                    _database.SavePartnerAgencyAsync(partnerAgency);
                }
            }

            partnerAgencyList.ItemsSource = partnerAgencies;
        }
```
It is the intitialistation of the list. It is really important to check if the retrieved list of partnerAgencies is either null or empty before doing anything.

## code review of my code

Database.cs:
In general, the code is well structured.
However, exception handling: Use specific exceptions rather than simply writing to the console. This allows errors to be handled more appropriately.

Model.cs:
On the whole, it's good, but to extend the use of this code, adding the possibility of length or format could be good.
It would also be better to name the model according to class, to make things clearer.

As for the rest, I think it's pretty well implemented.


I forgot to change the name of "model.cs" so I did it to make sur that my code is clear. 

## code review of my teamate's code

In general, the code is well structured.
You could add more comments to make your code more readable.
ExpertListView.xaml.cs : It might be worth considering adding exception handling to manage potential errors during database operations.
database.cs : It is essential to get rid of the database connection correctly when it is no longer needed. So perhaps you should implement the IDisposable interface and get rid of the connection in the Dispose method.
But otherwise the code seems really great to me.


My teamates respects the rules that we talked about with our team so it was easier to review

## General reflective section

This week I noticed that everyone in the group has made efforts to follow the rules that we have fixed.
So it was easier to work in a team than before. 
It was also quicker. 

So I think, when we work on a team, it is essential to fix some rules and to have the same organisation for our code. It is easier to review.
It was a good thing for me to join the blue team because I could learn how to work properly in a team. 
And it gave us the possibility to restart our organisation.



