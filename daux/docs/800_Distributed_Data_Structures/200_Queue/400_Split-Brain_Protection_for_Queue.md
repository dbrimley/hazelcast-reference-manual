
Queues can be configured to check for a minimum number of available members before applying queue operations (see [Split-Brain Protection](/2600_Network_Partitioning/200_Split-Brain_Protection.md)). This is a check to avoid performing successful queue operations on all parts of a cluster during a network partition. 

Following is a list of methods that now support quorum checks. The list is grouped by quorum type. 

- WRITE, READ_WRITE
    - `Collection#addAll`
    - `Collection#removeAll`, `Collection#retainAll`
    - `BlockingQueue#offer`, `BlockingQueue#add`, `BlockingQueue#put`
    - `BlockingQueue#drainTo`
    - `IQueue#poll`, `Queue#remove`, `IQueue#take`
    - `BlockingQueue#remove`
- READ, READ_WRITE
    - `Collection#clear`
    - `Collection#containsAll`, `BlockingQueue#contains`
    - `Collection#isEmpty`
    - `Collection#iterator`, `Collection#toArray`
    - `Queue#peek`, `Queue#element`
    - `Collection#size`
    - `BlockingQueue#remainingCapacity`