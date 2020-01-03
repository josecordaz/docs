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

ex, err := os.Executable()
if err != nil {
	return err
}
exPath := filepath.Dir(ex)

f, err := os.OpenFile(exPath+string(os.PathSeparator)+"testlogfile", os.O_RDWR|os.O_CREATE|os.O_APPEND, 0755)
if err != nil {
    log.Fatalf("error opening file: %v", err)
}
defer f.Close()

log.SetOutput(f)

log.Println("test")
```