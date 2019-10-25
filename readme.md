# Double Linked File List
Each entry is a file, with `id` as its filename.  
A simple database solution, but highly scalable.  

## Usage
```js
const LinkedFileList = require('linkedfilelist');
db = LinkedFileList('path_to_your_database/');

const id = db.add({payload: "slap like now"});
db.add({payload: "send bass"});
db.add({payload: "the licc", time: 44});
db.add({payload: "omg", time: 20});
db.display();

db.delete(id);
db.display();

const id_2 = db.add({payload: "slap like now"});
db.modify(id_2, {payload: "slap like now plz"});
db.display();

db.git('commit message'); // this message is shell-quoted  

db.diagnose();
```

## Features
* Dynamic filename length, grows as the database grows.  
* Each entry has a timestamp, and the list is sorted by time.  

## Drawbacks
A large number of small files may occupy extra space on large-cluster file systems, but this strategy ensures low time complexity of insertion and deletion.  
