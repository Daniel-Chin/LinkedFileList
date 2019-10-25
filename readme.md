# Double Linked File List
Each entry is a file, with `id` as its filename.  
A simple database solution, but highly scalable.  

## Usage
Code:  
```js
const LinkedFileList = require('linkedfilelist');
db = new LinkedFileList('path_to_your_database/');

const id = db.add({payload: "slap like now"});
db.add({payload: "send bass"});
db.add({payload: "the licc", time: 44});
db.add({payload: "omg", time: 20});
db.display();
```
Output:  
```
payload         time            id      prev            next
omg             20              kkp     __head__        ne3
the licc        44              ne3     kkp             crw
slap like now   1572019135723   crw     ne3             d95
send bass       1572019135740   d95     crw             __tail__
```
Code:  
```js
db.delete(id);
db.display();
```
Output:  
```
payload         time            id      prev            next
omg             20              kkp     __head__        ne3
the licc        44              ne3     kkp             crw
send bass       1572019135740   d95     crw             __tail__
```
Code: 
```js
const id_2 = db.add({payload: "slap like now"});
db.modify(id_2, {payload: "slap like now plz"});
db.display();
```
Output: 
```
payload                 time            id      prev            next
omg                     20              kkp     __head__        ne3
the licc                44              ne3     kkp             d95
send bass               1572019135740   d95     ne3             iar
slap like now plz       1572019306398   iar     d95             __tail__
```
More methods: 
```js
console.log(db.commit('commit message')); // this message is shell-quoted  
db.diagnose();  // diagnose the database for problems
const old_url = db.gitConfig('--get remote.origin.url');
db.gitConfig('remote.origin.url "My New URL"');
db.push();  // git push
```

## Features
* Dynamic filename length, grows as the database grows.  
* Each entry has a timestamp, and the list is sorted by time.  

## Drawbacks
A large number of small files may occupy extra space on large-cluster file systems, but this strategy ensures low time complexity of insertion and deletion.  
