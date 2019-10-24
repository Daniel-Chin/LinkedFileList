# Double Linked File List
Each entry is a file, with `id` as its filename.  
A simple database solution, but highly scalable.  

## Features
* Dynamic filename length, grows as the database grows.  
* Each entry has a timestamp, and the list is sorted by time.  

## Drawbacks
A large number of small files may occupy extra space on large-cluster file systems, but this strategy ensures low time complexity of insertion and deletion.  
