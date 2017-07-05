- python pip 安装出现 
```
"UnicodeDecodeError: 'ascii' codec can't decode byte 0xcd in position 7: ordinal not in range(128)" 
```
错误

- 解决方案

python目录 Python27\Lib\site-packages 建一个文件sitecustomize.py 
内容写：
```
import sys 
sys.setdefaultencoding('gb2312') 
```