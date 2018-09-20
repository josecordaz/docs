### Delete a local branch

```bash
    git branch -d the_local_branch
```

### Delete remote branch

```bash
    git push origin --delete the_remote_branch
```
### Marshall golang

```go
strObj, err := json.MarshalIndent(obj, "", " ")
if err != nil {
    panic(err)
}
```

### Unmarshall golang

```go
if err := json.Unmarshal(byt, &dat); err != nil {
     panic(err)
}
fmt.Println(dat)
```
