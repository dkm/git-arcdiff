git arcdiff
-----------

This is a simple wrapper for the [arc](https://secure.phabricator.com/book/phabricator/article/arcanist_diff/) command provided by [phabricator](https://phacility.com/phabricator/).

```
usage: git arcdiff [--dryrun] [--verbose] [--arc <ARC_PATH>] [--depends-on <DIFF_ID>] [--no-add-diffid] [--no-create-branch] [--update <DIFF_ID>] [<base>] <upstream> <branch>
   or: git arcdiff [--dryrun] [--verbose] [--arc <ARC_PATH>] --continue
   or: git arcdiff [--dryrun] [--verbose] [--arc <ARC_PATH>] [--no-force-request-review] [--no-add-diffid] --update-current
   or: git arcdiff [--dryrun] [--verbose] [--arc <ARC_PATH>] [--no-force-request-review]
   or: git arcdiff [--dryrun] [--verbose] [--arc <ARC_PATH>] --add-diffid-in-head <DIFF_ID>
   or: git arcdiff [--dryrun] [--verbose] --abort

Available options are
    -v, --verbose         display some garbage
    --no-create-branch    do not create a branch for the new code review
    --depends-on ...      add dependency on given existing code review
    --continue            continue after fixing a failed rebase
    --dryrun              only pretends to do something
    --update-current      update the existing code review bound to current checked out branch
    --update ...          same behavior as for creating a new review, but updates an existing review
    --no-force-request-review
                          when updating, do not force the review state.
    --abort               rolls back to state before previous arcdiff command
    --arc ...             path to the arc command
    --no-add-diffid       when updating/creating a review, do not modify the original commit message to add reference to code review
    --add-diffid-in-head ...
                          add a reference to differential revision in commit message of HEAD
```

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
