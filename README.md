# pyconpty

PyConPty is a wrapper around Windows native ConPty functionality. It was developed to enable the Windows terminal functionality in the DWService Agent. This project is still in the early stages but is fully functional. 

## Usage

A simple example of usage is the following. In more advanced uses the read and write would be handled on seperate threads. In addition remember the output contains VT sequeces so if connected to something like stdout of a python script in the Windows cmd prompt you will see a bunch of *junk*

```python
from pyconpty import conpty

pty = conpty.ConPty('cmd.exe', 90, 66)
pty.start()
time.sleep(0.1)
print(pty.read())
pty.write('whoami\r\n')
print(pty.read())
```
