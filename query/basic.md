# Perform some basic queries
A core functionality of ancpBIDS is to extract information from datasets. With the **layout** now held in-memory, we can use several built-in functions to extract useful information from the dataset; for example, accesing **common entities** such as Subjects, Tasks, and Runs. These simple queries are build in as ´layout.get_"NameOfTheEntity"()´. If the entity does not exist in the dataset or the name is not properly written, the query will return an empty list ´[]´. 


* **Get all subjects in the dataset**
  
````{tab-set}
```{tab-item} MEG

    subs = layout.get_subjects()
    print(subs)

    # Output: 
    #['009', '012', '013', '014', '015', '016', '017', '018', '019', '020', '021', '022', '023', '024', '025', '026', '027', '028', '029', '030', '031']

```

```{tab-item} MRI

    subs=layout.get_subjects()
    print(subs)

    #Output:
    # ['01', '02', '03', '04', '05', '06', '07', '08', '09', '10', '11', '12', '13', '14', '15', '16']

```
````


* **Find how many runs there are**

  
````{tab-set}
```{tab-item} MEG

    runs=layout.get_runs()
    print(runs)
    #Output
    #['1']

```

```{tab-item} MRI

    sruns=layout.get_runs()
    print(runs)
    #Output:
    #['01', '02', '03']

```
````

_Note that the returned runs are collected over all subjects and it is not guaranteed that each participant has the same number of runs._


* **Check out the tasks of the experiment**

````{tab-set}
```{tab-item} MEG

    tasks = layout.get_tasks()
    print(tasks)

    #Output:
    #['deduction','induction']

```

```{tab-item} MRI

    task = layout.get_task()
    print(task)

    #Output:
    #['mixedgamblestask']

```
````

## Query entities
If you want to check which entities exist in your dataset, you can use the following function to receive a dictionary with all entities in the dataset and its respective values.


````{tab-set}
```{tab-item} MEG

    avail_entitities=layout.get_entities()
    print("Entities: ", list(avail_entitities.keys()))
    print("Value of task: ", avail_entitities['task'])

    #Output:
    #Entities:  ['sub', 'ses', 'task', 'run', 'desc']
    #Value of task:  {'deduction', 'induction'}

```

```{tab-item} MRI

    avail_entitities=layout.get_entities()
    print("Entities: ", list(avail_entitities.keys()))
    print("Value of task: ", avail_entitities['task'])

    #Output:
    #Entities:  ['task', 'sub', 'run', 'ds', 'type']
    #Value of task:  {'mixedgamblestask'}

```
````
## Next Section
In the next section we will continue with more advanced queries using multiple filtering parameters and specific BIDS Key-value pairs.
