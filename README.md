# Many-to-many Object Relationships Lab

A small Python model for building contracts between books and authors. It
demonstrates a many-to-many relationship: authors can have many books through
contracts, and books can have many authors through contracts.

## What it does

- `Author(name)` — has `contracts()`, `books()`, `sign_contract(book, date, royalties)`,
  and `total_royalties()`.
- `Book(title)` — has `contracts()` and `authors()`.
- `Contract(author, book, date, royalties)` — the join between `Author` and `Book`.
  Validates that `author` is an `Author`, `book` is a `Book`, `date` is a `str`,
  and `royalties` is an `int`. Also has `Contract.contracts_by_date(date)`.

```python
from many_to_many import Author, Book

author = Author("Octavia Butler")
book = Book("Kindred")
contract = author.sign_contract(book, "01/01/2001", 50000)

author.books()            # [<Book: Kindred>]
book.authors()            # [<Author: Octavia Butler>]
author.total_royalties()  # 50000
```

## The Scenario 

We are tasked with building a model to aid in building contracts for books with 
multiple authors. As a part of this model we need to create an Author model, a Book 
model and a Contract model. Authors can have many books through contracts, and books 
can have many authors through contacts.

## Tools & Resources 
- [Github Repo](https://github.com/learn-co-curriculum/python-oo-many-to-many-book-contracts-lab)
- [Python classes](https://docs.python.org/3/tutorial/classes.html)

## Instructions

### Task 1: Define the Problem

Build a model a many to many relationship between Books and Authors:

* Build Book class
* Build Author class
* Build Contract class
* Build connecting methods between all

### Task 2: Determine the Design

#### Book:
* Attributes:
  * title (string)
  * all (array) 
* Methods:
  * contracts()
  * authors()

#### Authors:
* Attributes:
  * name (string)
  * all (array)
* Methods:
  * contracts()
  * books()
  * sign_contracts(book,date,royalties)
  * total_royalties()

#### Contracts:
* Attributes:
  * author (Author class), 
  * book (Book class), 
  * date (string), 
  * royalties (integer)
  * all (array)
* Methods:
  * contracts_by_date()

### Task 3: Develop, Test, and Refine the Code

#### Step 1: Create feature branch

#### Step 2: Create Book class

* `__init__`: title
* Class attributes- all
* Methods:
  * contracts()- This method should return a list of related contracts
  * authors()- This method should return a list of related authors using the Contract class as an intermediary

#### Step 3: Authors

* `__init__`: name (string)
* Class attributes- all
* Methods:
  * contracts()- This method should return a list of related contracts
  * books()- This method should return a list of related books using the Contract class as an intermediary
  * sign_contracts(book,date,royalties)- This method should create and return a new Contract object between the author and the specified book with the specified date and royalties
  * total_royalties()- This method should return the total amount of royalties that the author has earned from all of their contracts

#### Step 4: Contracts

* `__init__`:
  * author
  * book
  * date 
  * royalties 
* Class attributes: all
* Properties: All properties should raise an exception if not valid
  * author: Is an instance of Author class
  * book:  Is an instance of Book class
  * date: Is an instance of a str
  * royalties:  Is an instance of an int
* Class Methods: contracts_by_date()- This method should return all contracts that have the same date as the date passed into the method

#### Step 6: Push feature branch and open a PR on GitHub

#### Step 7: Merge to main

### Task 4: Document and Maintain

Best Practice documentation steps:
* Add comments to the code to explain purpose and logic, clarifying intent and functionality of your code to other developers.
* Update README text to reflect the functionality of the application following https://makeareadme.com. 
  * Add screenshot of completed work included in Markdown in README.
* Delete any stale branches on GitHub
* Remove unnecessary/commented out code
* If needed, update git ignore to remove sensitive data

## Important Submission Note

Before you submit your solution, you need to save your progress with git.

* Add your changes to the staging area by executing git add .
* Create a commit by executing git commit -m "Your commit message"
* Push your commits to GitHub by executing git push origin main
