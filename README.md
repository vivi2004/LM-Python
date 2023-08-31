class Library:
    def __init__(self, list_of_books):
        self.books = list_of_books
        self.issued_books = {}

    def displayAvailableBooks(self):
        print("Here are the list of books available:")
        for book in self.books:
            print(book)

    def borrowBook(self, student_name, book_name):
        if book_name in self.books:
            self.books.remove(book_name)
            self.issued_books[book_name] = student_name
            print(f"{student_name} has borrowed {book_name}")
        else:
            print(f"Sorry, {book_name}  it's  not available for borrowing.")

    def returnBook(self, book_name):
        if book_name in self.issued_books:
            student_name = self.issued_books.pop(book_name)
            self.books.append(book_name)
            print(f"{book_name} has been returned by {student_name}")
        else:
            print(f"{book_name} was not borrowed from this library.")

    def donateBook(self, book_name):
        self.books.append(book_name)
        print(f"{book_name} has been donated and added to the library.")

class Student:
    def requestBook(self):
        return input("Enter the name of the book you want to borrow: ")

    def returnBook(self):
        student_name = input("Enter your name: ")
        book_name = input("Enter the name of the book you want to return: ")
        return student_name, book_name

    def donateBook(self):
        return input("Enter the name of the book you want to donate: ")

# Main Execution
if __name__ == "__main__":
    book_list = ["Algorithm_I", "Discrete mathematics ", "Python", "MADE EASY ", "Flammingo","HELEN KELLER","The first Door","The atom of chioces ","The magnus of Cartus"]
    IIITlibrary = Library(book_list)
    student = Student()

    while True:
        print("\nHere are the option's :")
        print("1. Display available books")
        print("2.  Do you want to borrow a book")
        print("3.   you want to return  a book")
        print("4.   You want to donate  a book")
        print("5. Display issued book tracking")
        print("6. Exit")
        choice = int(input("Enter your choice: "))

        if choice == 1:
            IIITlibrary.displayAvailableBooks()
        elif choice == 2:
            book_name = student.requestBook()
            IIITlibrary.borrowBook(student.__class__.__name__, book_name)
        elif choice == 3:
            student_name, book_name = student.returnBook()
            IIITlibrary.returnBook(book_name)
        elif choice == 4:
            book_name = student.donateBook()
            IIITlibrary.donateBook(book_name)
        elif choice == 5:
            print("Issued book tracking:")
            print(IIITlibrary.issued_books)
        elif choice == 6:
            print("Exiting the program.")
            break
        else:
            print("Invalid choice. Please choose a valid option.")


        
