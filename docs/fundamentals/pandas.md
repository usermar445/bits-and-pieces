# Cheatsheet Pandas

## Indexing and selection

- column based seleciton (contrary to Numpy): `df['column1']` selects the column
- Dictionary-style selection: `df['column_name']['index']`
- Explicit indexing (using labels): `df.loc['index', 'column_name']`
- Implicit indexing (using positions): `df.iloc[row, column]`

**Attention:** if indexes are integers, selecting is still done explicitly. 

## Slicing and masking

- Explicit slicing (refers to rows): `df['row0':'row1']`
- Implicit slicing (refers to positions: `df[0:20]`

**Important:** explicit slicing *includes* the upper limit, whereas *implicit* excludes the upper limit.   
**Also:** by default, if indexes are *integers* slicing is done **implicitly** if not specified otherwise. 
**But not when selecting**


## Operations
Preserve and align indexes. If labels to not align, still an output is generated but with `NaN` values.

## Handling missing data

- `None` python null value; usually throws an error if arithmetic operation is performed
- `NaN` (=not a number) is a numerical value (floating point value); does not throw an error

Used almost interchangably in Pandas. Pandas converts all number columns to floating point values if they contain `NaN`.


## Merge and join
`join()` is a 'special case' of `merge()` that performs a join on indexes (if not specified other).

## Aggregation


## String manipulation


## Multi-index





