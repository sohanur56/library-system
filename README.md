class library:
    book_list=[]
    @classmethod
    def entry_book(self,book):
        self.book_list.append(book)
    
    def view_all_books(self):
        if not self.book_list:
            print('no book is there in the library')
        else:
            for book in self.book_list:
                book.view_book_info()
  
class book:
    def __init__(self,book_id,title,author,availability=True):
        self.__book_id=book_id
        self.__title=title
        self.__author=author
        self.__availability=availability
        library.entry_book(self)
    
    def get_book_id(self):
        return self.__book_id

    def borrow_book(self):
        if self.__availability:
            self.__availability=False
            print(f'{self.__title} is borrowed')
        else:
            print('not available right now') 
    
    def return_book(self):
        if not self.__availability:
            self.__availability=True

        else:
            print(f'{self.__title} was not borrowed')

    
    
    def view_book_info(self):
        print(f'book_id is:{self.__book_id}, title is:{self.__title},author is:{self.__author}, availability is:{self.__availability}')


def menu_system():
     
    while True:
        print('menu driven system:')
        print('1.view all books')
        print('2.borrow book')
        print('3.return book')
        print('4.exit')

        pressed =print(input('select from 1 to 4: '))

        if pressed==1:
            if library.book_list:
                for book in library.book_list:
                    print(book.view_book_info)
            else:
                print('no book available')
        elif pressed==2:
            book_id=print(input('give book id: '))
            for bi in library.book_list:
                if bi.get_book_id()==book_id:
                    bi.borrow_book()
                    print(f'book {book_id} is borrowed')
                else:
                    print('invalid book id')

        elif pressed==3:
            returned_book=print(input('give return book id: '))
            for rtd_book in library.book_list:
                if rtd_book.get_book_id()==returned_book:
                    rtd_book.return_book()
                    print(f'book {returned_book} is returned')
                else:
                    print('invalid book id')
        elif pressed==4:
            print('exiting the menu')
            break
            
def main():
    book(101,'math','sovon')
    book(102,'physics','hamim')
    book(103,'chemistry','naim')
    book(104,'english','sakir')

    menu_system()


          

                







    
        


    
        

