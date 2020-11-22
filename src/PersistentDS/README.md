# Persistent Data Structure

In normal DS when we change or update a particular value the entire DS gets changed. Consider an array `arr = [1, 2, 3, 4, 4]`, now if we want to update `arr[2]` to 6 it will become `[1, 2, 6, 4, 4]`. This final array now lost its pervious state. But in case of **Persistent DS** it will preserve it's previous states as well. 

Persistent Datastructure preserves all versions of itself
- Every update to the data structure creates a new version
- `Update(version, <value>): `  returns a new version

## Types of Persistence

### 1. Parital Persistence

 - Query any versions of the DS
 - Update only the latest version of DS

Let's say we have a series of versions as follows (in the form of Linked List):

v1 -> v2 -> v3 

Now if we want to make some changes we can only do that to the v3, so after this update we will have

v1 -> v2 -> v3 -> **v4**

Hence, all the versions will always be linearly ordered (due to the additional constraint)

### 2. Full Persistence

 - Query any versions of the DS (typical of any persistence)
 - Update any version of the DS

Let's say initially you only one version v1, and then you make an update you get

```
v1 -> v2
```

Now you apply another update but again to v1 (this was not possible in partial persistence) here it will branch off as show below

```
        v1
       /  \ 
     v2    v3

```

Again if we update v3 we will get:-

```
        v1
       /  \ 
     v2    v3
            \
            v4 
```

Hence, in full persistence the versions will form a tree. 

>A DS that supports full persistence will always support partial persistence.