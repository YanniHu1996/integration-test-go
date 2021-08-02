# integration-test-go

This is a demo for  full lifestyle for integration test

## Below is some question about integration test

- How to trigger test

- When the test is concurrent, how to handle it

- What is the principle of the test case? (How to make the test case is effective)

- How to write the test case with the format of BDD

- How the report the result of the test

- How to show the history

    - data schema
    - query
    - some function button 

- How to spend less time

I will use many techs to try to solve the problems above

## Below is some constraints

- No ops, I want to spend as little or no time maintaining the system as possible

- Closed to Github

## Here is some

### Regard repo as a k-v database

```sh
# write a value
echo {"id": 1, "name": "kenneth"} | git hash-object -w --stdin
# dcbfa843bfc2c0039e79d2c272bc022312f31ceb

## create a file save to staging area
git update-index --add --cacheinfo 100644 dcbfa843bfc2c0039e79d2c272bc022312f31ceb 1.json

## write content of staging area to tree
git write-tree
# 56cc45144f7700f907f1def3428818dd45b28312


## update file by fellow steps
echo "{"id": 1, "name": "kenneth truyers"}" | git hash-object -w --stdin
# 6ebd1e99cd13322fa6a54f8888b8b6e66864b5ea

git update-index --add --cacheinfo 100644 6ebd1e99cd13322fa6a54f8888b8b6e66864b5ea 1.json
git write-tree
# 66a2bc7dc637f68d14a3ff6b44f2b608499c7fb4

# commit 1st tree
echo "commit 1st version" | git commit-tree 56cc45144f7700f907f1def3428818dd45b28312
# 8a0e71572bd1184088a67c866921bb54a74e48b4

# commit 2nd tree
echo "commit 2nd version" | git commit-tree 66a2bc7dc637f68d14a3ff6b44f2b608499c7fb4 -p 8a0e7157
# 2f22426b8c00e25689d54cf409c78d9f0b59ec8a

# show commit above
git log --stat 2f22426b8c00e25689d54cf409c78d9f0b59ec8a

```

###