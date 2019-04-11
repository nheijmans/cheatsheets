## Cheatsheet: PythonM
#### Start http server python 2
```python -m "SimpleHTTPServer" 8000```

#### Start http server python 3 
```python -m http.server 8000 --bind 127.0.0.1```

#### Allow piping output to tee and save to file while monitoring
```python -u <yourscript.py> | tee output.txt```
