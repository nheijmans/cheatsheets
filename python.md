## Cheatsheet: PythonM
#### Start http server python 2
```python -m "SimpleHTTPServer" 8000```

#### Start http server python 3 
```python -m http.server 8000 --bind 127.0.0.1```

#### Allow piping output to tee and save to file while monitoring
```python -u <yourscript.py> | tee output.txt```

#### Get datetime string for logging, without milliseconds
```
>>> from datetime import datetime
>>> dt = str(datetime.now())[:-7]
>>> print(dt)
'2019-05-28 15:34:37'

```

#### Re-install pip in a virtual environment
```
curl https://bootstrap.pypa.io/get-pip.py -o get-pip.py
python3 get-pip.py --force-reinstall
```
