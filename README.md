# Fix ODO Source with buugfixes
## In ODO Source Before Installing it
## In Utils.py Line : 130 ->  return inspect.getfullargspec(func).args
## Error: CSV to sqlite fails with "TypeError: can only concatenate list (not "TextFileReader") to list"
## In /backends/csv.py 
## Line : 347

    with c.open() as f:
        result = pd.read_csv(f,
                           header=header,
                           sep=sep,
                           encoding=encoding,
                           dtype=dtypes,
                           parse_dates=parse_dates,
                           names=names,
                           chunksize=chunksize,
                           usecols=usecols,
                           **kwargs)
        if chunksize is not None:
            result = pd.concat(result, ignore_index=True)
        return result
## Line : 374 ->  data = [first] + [rest]
