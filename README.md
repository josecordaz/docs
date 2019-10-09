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

### Log info to file

```go
f, err := os.OpenFile("testlogfile", os.O_RDWR|os.O_CREATE|os.O_APPEND, 0666)
if err != nil {
    log.Fatalf("error opening file: %v", err)
}
defer f.Close()

log.SetOutput(f)

log.Println("test")
```