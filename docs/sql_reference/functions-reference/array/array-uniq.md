---
layout: default
title: ARRAY_UNIQ
description: Reference material for ARRAY_UNIQ function
grand_parent: SQL functions
parent: Array functions
---

# ARRAY\_UNIQ

If one argument is passed, returns the number of different elements in the array. If multiple arguments are passed, returns the number of different tuples of elements at corresponding positions in multiple arrays.

## Syntax
{: .no_toc}

```sql
ARRAY_UNIQ(<arr> [, ...n])
```

| Parameter        | Description                         |
| :---------------- | :----------------------------------- |
| `<arr> [, ...n]` | The array or arrays to be analyzed. |

## Return Types
The return type for this function is `ARRAY`.

## Example
{: .no_toc}

```sql
SELECT
	ARRAY_UNIQ([ 1, 2, 4, 5 ]) AS res;
```

**Returns**: `4`

## Example&ndash;using multiple arrays
{: .no_toc}

When using multiple arrays, `ARRAY_UNIQ` evaluates all the elements at a specific index as tuples for counting the unique values.&#x20;

For example, two arrays \[1,1,1,1] and \[1,1,1,2] would be evaluated as individual tuples (1,1), (1,1), (1,1), and (1,2). There are 2 unique tuples, so `ARRAY_UNIQ` would return a value of 2.

```
SELECT
	ARRAY_UNIQ ([ 1, 1, 1, 1 ], [ 1, 1, 1, 2 ]) AS levels;
```

**Returns**: `2`

In the example below, there are three different video game usernames across all of the elements of the given arrays. However, there are only two unique tuples, ('tonytaylor', 'ruthgill') and ('tonytaylor', 'ywilson').

```
SELECT
	ARRAY_UNIQ (
		[ 'tonytaylor',
		'tonytaylor',
		'tonytaylor',
		'tonytaylor' ],
		[ 'ruthgill',
		'ruthgill',
		'ywilson',
		'ywilson' ]
	) AS res;
```

**Returns**: `2`