git arcdiff
-----------

This is a simple wrapper for the [arc](https://secure.phabricator.com/book/phabricator/article/arcanist_diff/) command provided by [phabricator](https://phacility.com/phabricator/).

Quickstart
----------

# Single review for last commit

## Create new review
```
$ git arcdiff origin/master HEAD^ HEAD
```

## Update existing review
```
$ git arcdiff --update D1234 origin/master HEAD^ HEAD
```

# Several commit review

## Create new review for commit A to B
```
 o---o---o---o---o master (HEAD)
     A       B
      
$ git arcdiff origin/master A^ B
```

## Update existing review with extra commits (from A to C)
```
 o---o---o---o---o--o---o master (HEAD)
     A       B   C

$ git arcdiff --update D1234 origin/master A^ C
```
