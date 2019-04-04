# React

<details><summary>Statefull Component</summary>

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
                {books.map( (book, i) => <BookItem key={`${book.isbn}: ${i}`} book={book} />)}
            </div> : 
            <div style={{padding: '5px'}}>No books...</div>
    }
}

export default BookList
```
</details>

<details><summary>Stateless Component</summary>

```javascript
# BookItem.js
import React from 'react'

const BookItem = ({book}) => 
    <div>
        title: {book.title},&nbsp;
        <a href={book.previewLink}>{book.previewLink}</a>
    </div>

export default BookItem
```
</details>
<details><summary>Arrow function</summary>

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
