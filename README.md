# B-Tree-Implementation
In this project, I have created modules that deal with the insertion and deletion of entries in the B+ Tree. I have implemented a full insert using the methods- insert () and _insert() , and naive delete using the method ‘NaiveDelete()’ in B+ Tree Structure.

### insert() method

In this method, we pass the parameters <key, recordID>. Initially, we check if the header exists or not as for the first time, B+ Tree would be empty and header would be pointing to an invalid page. We create a new leaf page, insert the entry, set the previous and next pointers. We also update the header to point to the newly created leaf page.

If the header already exists, we call the _insert(), where the further insertion takes place and that method return a key data entry to check if the leaf split has occurred. If leaf split has occurred, the index will be updated.

### _insert() method

The _insert() function checks whether the current page is a Leaf or an Index. In case, it is a leaf page, it checks for space in the page and inserts into it. Once the leaf page becomes full, we need to split the data into a newly created leaf. The records in the first leaf page is counted and the middle record in the first leaf page is found. We divide the counter into half and insert the second half of records into the new leaf and delete them from the first leaf page. The new key is then inserted into the page accordingly by comparing the key with last record in the first leaf page. We also need to copy up the first entry into the index above, which if not present at the very first leaf split, must be created and made to point to the two leaf pages, and also update the header page.

If it is an index page, we check if the split has occurred. If the split has occurred, we insert and update the index. In case the index is full, we split the index by copying all entries into new leaf and then rewriting the first half entries back into

the old index. If the root was split, then we create a new root and move up the first entry into new root and point the header page to new root.

### NaiveDelete() method

We search the leaf page containing the key to be deleted. Using an iterator, we traverse to the end of the leaf. We compare the key with the iterator key and then perform deletion. We use recursion to remove all occurrences of the key, which means the duplicate values are also deleted.
