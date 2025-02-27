## [[Linux]]  [[compress and extract]]

### How to compress

```bash
tar -czvf name-of-archive.tar.gz /path/to/directory-or-file 
``` 
    
## Extract in the Current Directory
    
```bash
tar -xvzf example1.tar.gz
```
    
### Extract Files to a Specific Directory
    
```bash
tar -xvzf example1.tar.gz -C ./Documents
```  
  
ls -al  
ls -l  
alias --save ll="ls -al"  
fish_update_completions