**To create the LibraryDB type the following command:**

use LibraryDB
<!-- if for some reason you get a reference error use showdbs then useLibrary again but with space between use and Library this time -->

**To create the Books collection type the following command:**
 oh and here is a tip for beginners like me,mongoShell does not allow to use the ctr + v shortcut so you have to right click on **the shell Terminal once you have copied something:**

db.Books.insertMany([{ _id: 1, title: "1984", author_id: 1, genres: ["Dystopian", "Political Fiction"], published_year: 1949, available: true }, { _id: 2, title: "To Kill a Mockingbird", author_id: 2, genres: ["Southern Gothic", "Bildungsroman"], published_year: 1960, available: true }, { _id: 3, title: "The Great Gatsby", author_id: 3, genres: ["Tragedy"], published_year: 1925, available: true }, { _id: 4, title: "Brave New World", author_id: 4, genres: ["Dystopian", "Science Fiction"], published_year: 1932, available: true }, { _id: 5, title: "The Catcher in the Rye", author_id: 5, genres: ["Realist Novel", "Bildungsroman"], published_year: 1951, available: true }, { _id: 6, title: "Moby-Dick", author_id: 6, genres: ["Adventure Fiction"], published_year: 1851, available: true }, { _id: 7, title: "Pride and Prejudice", author_id: 7, genres: ["Romantic Novel"], published_year: 1813, available: true }, { _id: 8, title: "War and Peace", author_id: 8, genres: ["Historical Novel"], published_year: 1869, available: true }, { _id: 9, title: "Crime and Punishment", author_id: 9, genres: ["Philosophical Novel"], published_year: 1866, available: true }, { _id: 10, title: "The Hobbit", author_id: 10, genres: ["Fantasy"], published_year: 1937, available: true }])

To create the Authors collection type the following command:

db.Authors.insertMany([{ _id: 1, name: "George Orwell", nationality: "British", birth_year: 1903, death_year: 1950 }, { _id: 2, name: "Harper Lee", nationality: "American", birth_year: 1926, death_year: 2016 }, { _id: 3, name: "F. Scott Fitzgerald", nationality: "American", birth_year: 1896, death_year: 1940 }, { _id: 4, name: "Aldous Huxley", nationality: "British", birth_year: 1894, death_year: 1963 }, { _id: 5, name: "J.D. Salinger", nationality: "American", birth_year: 1919, death_year: 2010 }, { _id: 6, name: "Herman Melville", nationality: "American", birth_year: 1819, death_year: 1891 }, { _id: 7, name: "Jane Austen", nationality: "British", birth_year: 1775, death_year: 1817 }, { _id: 8, name: "Leo Tolstoy", nationality: "Russian", birth_year: 1828, death_year: 1910 }, { _id: 9, name: "Fyodor Dostoevsky", nationality: "Russian", birth_year: 1821, death_year: 1881 }, { _id: 10, name: "J.R.R. Tolkien", nationality: "British", birth_year: 1892, death_year: 1973 }])

**To finally create the Patrons collection type the following command:**

db.Patrons.insertMany([{ _id: 1, name: "Alice Johnson", email: "alice@example.com", borrowed_books: [] }, { _id: 2, name: "Bob Smith", email: "bob@example.com", borrowed_books: [1, 2] }, { _id: 3, name: "Carol White", email: "carol@example.com", borrowed_books: [] }, { _id: 4, name: "David Brown", email: "david@example.com", borrowed_books: [3] }, { _id: 5, name: "Eve Davis", email: "eve@example.com", borrowed_books: [] }, { _id: 6, name: "Frank Moore", email: "frank@example.com", borrowed_books: [4, 5] }, { _id: 7, name: "Grace Miller", email: "grace@example.com", borrowed_books: [] }, { _id: 8, name: "Hank Wilson", email: "hank@example.com", borrowed_books: [6] }, { _id: 9, name: "Ivy Taylor", email: "ivy@example.com", borrowed_books: [] }, { _id: 10, name: "Jack Anderson", email: "jack@example.com", borrowed_books: [7, 8] }])

**To find a Specific Book by Title in this case To Kill a Mockingbird type the following command:**

db.Books.find({title: "To Kill a Mockingbird"})

**To find all the books a specific author wrote in my case I will be using athor id so just type the following command:**

db.Books.find({author_id: 5})

**To find all available books type the following command:**

db.Books.find({available:true})


**To display every book in the collection type the following command:**

db.Books.find()

**To find books after a certain date 1950 in my case type the following command:**

db.Books.find({published_year:{$gt:1950}})

**To find an author based on their nationality in my case all american authors type the following command:**

db.Authors.find({nationality:{$eq:"American"}})

**To find all books that are available and published after 1950 in my case type the following command:**

db.Books.find({available:true},{published_year:1950}) or
 db.Books.find({ available: true, published_year: { $gt: 1950 } })
<!-- Note this will return books published before and after 1950,I made a mistake-->

**To find all authors named George in my case type the following command:**

db.Authors.find({name:{$regex:"George"}})

**To update a book's availability to borrowed in my case type the following command:**

db.Books.updateOne({_id:3},{$set:{avalable:false}}) or 

db.Books.updateOne({_id:3},{$set:{availability:"borrowed"}})
<!-- Note this will add a new field if it doesn't exist and because i got confused-->

**To add a genre to a book type the following command:**

db.Books.updateOne({_id:8},{$addToSet:{genre:'Fantasy'}})

**To add a borrowed book to a patron's record type the following command:**

db.Patrons.updateOne({_id:5},{$addToSet:{'borrowed_books':2}})

**To delete a book by its title type the following command:**

db.Books.deleteOne({title:'Brave New World'})

**To delete a Author via their id type the following command:**

db.Authors.deleteOne({_id:3})

**To increment the published year of 1869 by 1 in my case type the following command:**

db.Books.updateMany({published_year:1869},{$inc:{"published_year:":1}})

**To set all books to available type the following command:**
db.Books.updateMany({},{$set:{available:true}})