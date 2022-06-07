execnb
================

<!-- WARNING: THIS FILE WAS AUTOGENERATED! DO NOT EDIT! -->

## Install

Either:

    pip install execnb

or if you use conda:

    conda install -c fastai execnb

(You can replace `conda` with `mamba` in the line above if you have
mamba installed.)

## How to use

Use `CaptureShell` to run Jupyter code and capture notebook outputs,
without running a Jupyter server (or even having it installed):

``` python
s = CaptureShell()
s.run('1+1')
```

    [{'data': {'text/plain': ['2']},
      'metadata': {},
      'output_type': 'execute_result',
      'execution_count': 1}]

To execute a notebook and save it with outputs filled in, use `execute`:

``` python
try:
    s.execute('../tests/clean.ipynb', 'tmp.ipynb')
    print(read_nb('tmp.ipynb').cells[1].outputs)
finally: Path('tmp.ipynb').unlink()
```

    [{'data': {'text/plain': ['2']}, 'execution_count': 6, 'metadata': {}, 'output_type': 'execute_result'}, {'name': 'stdout', 'output_type': 'stream', 'text': ['1']}]