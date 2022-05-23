# Group Expense Tracker

The goal of this project is to create a simple expense tracker in which a group of people can manage their expenses and get a summary of their balance.


## Features - 

1. Ability to create a group
	- Each group should have a name and list of members
	- Whenever an expense is added within a group, the members of the expense who are not part of the group should automatically be added as a member.
	  For example - A user creates a group "Home" with members ["A", "B"] and later adds an expense which has user "C", the group members will be - ["A" "B", "C"]
2. Ability to add an expense within a group
	Structure of an expense - 
  
        {
          "name": "Fruits and Milk",
          "items": [{"name": "milk", "value": 50, "paid_by": [{"A": 40, "B": 10}], "owed_by": [{"A": 20,"B": 20, "C": 10}]},
                    {"name": "fruits", "value": 50, "paid_by": [{"A": 40}], "owed_by": [{"A": 10,"B": 30, "C": 10}]}]
        }
3. Ability to update an expense within a group
    - Structure same as add expense.
4. Ability to delete an expense within a group
5. Ability to get the balance of a group such that the balances are simplified. which means -
    - If A,B,C are in a group such that A owes B Rs 100, B owes C Rs 100 and C owes A Rs 100, the balance summary should show that A owes C Rs 100
    - The structure should be -

    	    {
            "name": "Home",
            "balances": {
              "A": {
                "total_balance": -100.0
                "owes_to": [{"C": 100}],
                "owed_by": []
              },
              "B": {
                "total_balance": 0.0
                "owes_to": [],
                "owed_by": []
              },
              "C": {
                "total_balance": 100.0
                "owes_by": [{"A": 100}],
                "owed_to": []
              }
            }
        	}



## Implementation Details -

1. Keep everything in memory. No need to use a database.
2. Create REST API for all the 5 features
3. The code should be clean and object oriented.
4. The system should be consistent always. If multiple people are trying to edit the same bill at the same time, we should take the edits one at at a time and the latest update should be applied. 
	For example - If inital expense is of Rs 100, and A is trying to update the bill to Rs 120, B is trying to update the bill to Rs 80, the system should apply updates sequencially and the balances should be consistent. [Hint - think about locking mechanisms to apply]


## Marking criteria -

### Your code should be clear and easy to understand:

- Avoids unnecessary complexity / over-engineering
- Brief comments are added where appropriate
- Broken into logical chunks
- Follows a module pattern

### Your code should be performant:

- Gives feedback to the user as soon as possible (perceived performance)
- Your code should be testable (but writing tests isn't necessary):
- Should be scalable - Adding new features should be easy and system remains consistent if alot of people are using at the same time.




