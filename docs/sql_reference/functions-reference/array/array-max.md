---
layout: default
title: ARRAY_MAX
description: Reference material for ARRAY_MAX function
grand_parent: SQL functions
parent: Array functions
---

# ARRAY\_MAX

Returns the maximum element in an array `<array>`.

## Syntax
{: .no_toc}

```sql
ARRAY_MAX(<array>)
```

## Parameters 
| Parameter | Description                                  | Supported input types |
| :--------- | :-------------------------------------------- | :-------|
| `<array>`   | The array or array-type column to be checked | `<array>` | 

## Return Types
`NUMERIC` 

## Example
{: .no_toc}

The following examples calculates the maximum number in the `levels` array: 
```sql
SELECT
	ARRAY_MAX([ 1, 2, 3, 4 ]) AS levels;
```

**Returns**: `4`