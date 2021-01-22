### <b>if</b>函数 
结构为 <br>
if <br>
elseif <br>
else <br>
end
```matlab
A = rand(4);
B = rand(4);
C = rand(4);

if isequal(size(A), size(B))
    D = [A;B];
elseif isequal(size(A), size(C))
    D = [A;C];
else
    disp('A and B and C are not match');
end
```

### <b>for</b>函数
可以用<b>break;</b>跳出循环 <br>
可以用<b>continue;</b>进行操作 <br>
```matlab
for i = 1:1:20
    % i = [5 8 9 10]
    语句
end
```
嵌套循环
```matlab
for i = 1:5
    for j = 1:5
        语句
    end
end
```
### <b>while</b>函数

```matlab
while ----
    语句
end
```

### <b>switch</b> 语句

```matlab
switch n
    case 1
        语句
    case 2
        语句
    otherwise
end
```

### 定义函数
matlab中第一个函数名和文件名应一致，子函数写在子文件中  <br>
函数调用时，只要文件在当前目录下，就可以调用
```matlab
function 函数名（参数表）
    语句
end
```
多个参数时
```matlab
function [std, var, min, max] = statistics_of_data(a,b)
    d = [a:b];
    standard_dev = std(d);
    variance = var(d);
    minimum = min(d);
    maximum = max(d);
end

% 调用
[a, b, c, d] = statistics_of_data(1,10);
```

返回值
return 做循环和递归的准出条件
```matlab
function ----
     语句
     return;
end
```





