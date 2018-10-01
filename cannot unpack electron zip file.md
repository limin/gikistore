
## Got error to pack desktop app with electron
```
• cannot unpack electron zip file, will be re-downloaded error=zip: not a valid zip file
  ⨯ zip: not a valid zip file
```

## solution
remove the cache 

```
$rm -fr ~/.cache/electron
$rm -fr ~/.cache/electron-builder
```