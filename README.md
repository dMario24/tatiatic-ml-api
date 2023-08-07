# ml-api

## ENV
- python 3.9

- pyenv
```
$ pyenv install --list
$ pyenv install 3.9.16
$ pyenv global 3.9.16
$ pyenv versions
pyenv versions
  system
  3.7.16
* 3.9.16 (set by /home/tom/.pyenv/version)
```

- pipenv
```
$ pip install pipenv
$ pipenv --python 3.9.16
$ pipenv shell
```

## DEV
```
$ pipenv shell
$ pipenv install fastapi
$ pip install "uvicorn[standard]"
```

## RUN
- uvicorn main:app --reload

## DEPLOY
```

```

## REF
- https://fastapi.tiangolo.com/ko/
