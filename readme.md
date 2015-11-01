# Environmental Override

Environmental Override makes it easy to set configuration values using environment variables.

## Quickstart

Say you had a configuration file setting a handful of settings:

```python
MY_GITHUB_NAME='coddingtonbear'
DEBUG_MODE=False
SOMETHING_SIZE=100
USER_TO_SOMETHING_MAP={
    'alpha': 'beta',
}
```

Environmental override makes it easy for you to override those settings by
adding the following code to the bottom of the above configuration file:

```python
from environmental_override import override

override(locals(), 'MY_PREFIX_')
```

Environment variables having a name starting with the prefix you define (in the
above example -- "MY_PREFIX_") will automatically be converted into local
variables.  Also, since environment variables are always strings, you can use
special key suffixes to convert the data into an appropriate type.

For example -- to change the github name, turn on debug mode, raise the
something size, and change the user to something map, you could set the
following environment variables:

```
MY_PREFIX_MY_GITHUB_NAME='somebody'
MY_PREFIX_DEBUG_MODE__BOOL=1
MY_PREFIX_SOMETHING_SIZE__INT=200
MY_PREFIX_USER_TO_SOMETHING_MAP__JSON='{"alpha": "beta", "delta": "gamma"}'
```
