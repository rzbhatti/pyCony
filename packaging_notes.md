# Packaging notes 

### git clone 
```shell
git clone git@github.com:rzbhatti/pyCony.git 
# or 
https://github.com/rzbhatti/pyCony.git
# or 
gh repo clone rzbhatti/pyCony
```


### Clean start 

```shell
rm -rf dist 
rm -rf pycony.egg-info 
rm -rf build
rm -rf pycony/__pycache__
```
Clean directory should look like this when run `tree pyCony`:

```
pyCony
├── LICENSE
├── README.md
├── packaging_notes.md
├── pycony
│   └── __init__.py
├── setup.py
└── test
    └── test.py
```

### Required packages 
```shell
pip install build
pip install twine
```

### Building package 
Run the build command:
```shell
python -m build
```
`Successfully built pycony-0.1.0.tar.gz and pycony-0.1.0-py3-none-any.whl`

The directory should look like this when run `tree pyCony`:

```
pyCony
├── LICENSE
├── README.md
├── dist
│   ├── pycony-0.1.0-py3-none-any.whl
│   └── pycony-0.1.0.tar.gz
├── packaging_notes.md
├── pycony
│   └── __init__.py
├── pycony.egg-info
│   ├── PKG-INFO
│   ├── SOURCES.txt
│   ├── dependency_links.txt
│   └── top_level.txt
├── setup.py
└── test
    └── test.py
```

### PyPI token setup 
Make sure that you have registered https://pypi.org/register
Setup API token https://pypi.org/manage/account, scroll all the way down to `API tokens`. 
and place it in `$HOME/.pypirc`

```
[pypi]
  username = <USER-NAME>
  password = pypi-<API-TOKEN>
```

### Uploading the package to PyPI

```shell
twine upload dist/*
# or for verbose output 
twine upload --verbose dist/*
```

The verbose output 
```shell
INFO     Using configuration from /Users/rzbhatti/.pypirc                                                                                
Uploading distributions to https://upload.pypi.org/legacy/
INFO     dist/pycony-0.1.0-py3-none-any.whl (4.3 KB)                                                                                     
INFO     dist/pycony-0.1.0.tar.gz (4.3 KB)                                                                                               
INFO     username set by command options                                                                                                 
INFO     password set from config file                                                                                                   
INFO     username: __token__                                                                                                             
INFO     password: <hidden>                                                                                                              
Uploading pycony-0.1.0-py3-none-any.whl
100% ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━ 9.9/9.9 kB • 00:00 • ?
INFO     Response from https://upload.pypi.org/legacy/:                                                                                  
         200 OK                                                                                                                          
INFO     <html>                                                                                                                          
          <head>                                                                                                                         
           <title>200 OK</title>                                                                                                         
          </head>                                                                                                                        
          <body>                                                                                                                         
           <h1>200 OK</h1>                                                                                                               
           <br/><br/>                                                                                                                    
                                                                                                                                         
                                                                                                                                         
                                                                                                                                         
          </body>                                                                                                                        
         </html>                                                                                                                         
Uploading pycony-0.1.0.tar.gz
100% ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━ 9.9/9.9 kB • 00:00 • ?
INFO     Response from https://upload.pypi.org/legacy/:                                                                                  
         200 OK                                                                                                                          
INFO     <html>                                                                                                                          
          <head>                                                                                                                         
           <title>200 OK</title>                                                                                                         
          </head>                                                                                                                        
          <body>                                                                                                                         
           <h1>200 OK</h1>                                                                                                               
           <br/><br/>                                                                                                                    
                                                                                                                                         
                                                                                                                                         
                                                                                                                                         
          </body>                                                                                                                        
         </html>                                                                                                                         

View at:
https://pypi.org/project/pycony/0.1.0/
```