To create the Books collection

To find a Specific Book by Title in this case To Kill a Mockingbird type the following command:

db.Books.find({title: "To Kill a Mockingbird"})

To find all the books a specific author wrote in my case I will be using athor id so just type the following command:

db.Books.find({author_id: 5})

To find all available books type the following command:

db.Books.find({available:true})

To update a book's availability to borrowed in my case type the following command:

db.Books.updateOne({_id:3}{$set:{avalable:false}}) or 

db.Books.updateOne({_id:3},{$set:{availability:"borrowed"}})
<!-- Note this will add a new field if it doesn't exist -->

To add a genre to a book type the following command:

db.Books.updateOne({_id:8},{$addToSet:{'Fantasy'}})

To add a borrowed book to a patron's record type the following command:

db.Patrons.updateOne({_id:5},{$addToSet:{'borrowed_books':2}})

To delete a book by its title type the following command:db 

db.Books.deleteOne({title:'Brave New World'})

To delete a Author via their id type the following command:

db.Authors.deleteOne({_id:3})

To find books after a certain date 1950 in my case type the following command:

db.Books.find({published_year:{$gt:1950}})

To find an author based on their nationality in my case all american authors type the following command:

db.Authors.find({nationality:{$eq:"American"}})