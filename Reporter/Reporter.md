# Questions

## About documents
1. How many documents were processed?
2. How many different documents were processed?
3. Day with most processments?
   1. documentRecords.GroupBy(Function(d) d.CreateTime.Date).OrderByDescending(Function(g) g.Count()).FirstOrDefault().Key.ToString()
4. Average number of documents process per day?
   1. documentRecords.GroupBy(Function(d) d.CreateTime.Date).Select(function(g) g.Count()).ToArray().Average()

## About classification
1. Average classification confidence per document type?

    For a particular document type...
2. Lowest classification confidence?
3. Lowest classification confidence without validation correction
4. Highest classification confidence with calssificaiton correction?
5. Range for classification Threshold?

## About Extraction
    For a particular document type...
1. Field with lowest confidence?
2. Fields average confidence?

    For a particular field
3. Lowest field confidence without validation correction
4. Highest field confidence with validation correction?