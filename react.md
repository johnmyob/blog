# Java Script

<details><summary>Sample</summary>

```javascript
// BookList.js
import React from 'react'
import { getIsbns } from './Utils'
import BookItem from './BookItem'

class BookList extends React.Component {
    state = {
        books: []
    }

    componentDidMount() {
        fetch('https://www.googleapis.com/books/v1/volumes?q=react+javcascript')
            .then( res => res.json() )
            .then( res => {
                let books = res.items.map( book => { 
                    return {
                        isbn: getIsbns(book),
                        title: book.volumeInfo.title,
                        previewLink: book.volumeInfo.previewLink
                    }
                })
                this.setState({ books }) 
            })
    }

    render() {
        let { books } = this.state
        return books && books.length > 0 ? 
            <div style={{padding: '5px'}}>
                Books:
                {books.map( book => <BookItem book={book} />)}
            </div> : 
            <div style={{padding: '5px'}}>No books...</div>
    }
}

export default BookList
```
```javascript
# BookItem.js
import React from 'react'

const BookItem = ({book}) => 
    <div key={book.isbn}>
        title: {book.title},&nbsp;
        <a href={book.previewLink}>{book.previewLink}</a>
    </div>

export default BookItem
```
```javascript
# Utils.js
const getIsbns = (book) => 
    book.volumeInfo.industryIdentifiers
        .reduce((acc, isbn) => { 
            const id = isbn.type + ': ' + isbn.identifier;  
            return acc.length > 0 ? acc + ", " + id : id 
        }, '')

export { getIsbns }
```

</details>
