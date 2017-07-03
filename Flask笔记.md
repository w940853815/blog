
---
Flask 使用上下文临时把某些对象 变为全局可访问


---

request 不可能是 全局变量。试想，在多线程服务器中，多个线程同时处理不同客户端发送的不同请求时， 每个线程看到的 request 对象必然不同。Falsk 使用上下文让特定的变量在一个线程中全局 可访问，与此同时却不会干扰其他线程

---


URL 映射是 URL 和视图函数之间的对应关系。 Flask 使用 app.route 修饰器或者非修饰器形式的 app.add_url_rule() 生成映射。

---

 app.url_map 查看Flask 程序中的 URL 映射


还有一种特殊的响应由abort函数生成，用于处理错误。在下面这个例子中，如果 URL 中 动态参数 id 对应的用户不存在，就返回状态码 404
    

---

Jinja2 能识别所有类型的变量，甚至是一些复杂的类型，例如列表、字典和对象，对象方法

```
<p>A value from an object's method: {{ myobj.somemethod() }}.</p>


Jinja2 还支持宏。宏类似于 Python 代码中的函数。例如：
    {% macro render_comment(comment) %}     
    <li>{{ comment }}</li> 
    {% endmacro %} 
     
    <ul> 
        {% for comment in comments %}
            {{ render_comment(comment) }}
        {% endfor %} 
    </ul>
为了重复使用宏，我们可以将其保存在单独的文件中，然后在需要使用的模板中导入：
{% import 'macros.html' as macros %} 
<ul>
     {% for comment in comments %}
        {{ macros.render_comment(comment) }}
            {% endfor %} 
</ul> `
```


---


有一个使用 JavaScript开发的优秀客户端开源代码库，名为moment.js（http://momentjs. com/），它可以在浏览器中渲染日期和时间。Flask-Moment 是一个 Flask 程序扩展，能把 moment.js 集成到 Jinja2 模板中。

---

post请求刷新警告信息
用户输入名字后提交表单，然后点击浏览器的刷新按钮，会看到一个莫名其妙的警告，要求在再次提交表单之前进行确认。之所以出现这种情况，是因为刷新页面时浏览器会重新发送之前已经发送过的最后一个请求。
基于这个原因，最好别让 Web 程序把 POST 请 求作为浏览器发送的最后一个请求。
这种需求的实现方式是，使用重定向作为 POST 请求的响应，而不是使用常规响应。重定向是一种特殊的响应，响应内容是URL，而不是包含HTML代码的字符串。浏览器收到这种响应时，会向重定向的 URL 发起 GET 请求，显示页面的内容。
程序可以把数据存储在用户会话中，在请求之间“记住”数据。
'''
@app.route('/', methods=['GET', 'POST']) 
def index():
    form = NameForm()
    if form.validate_on_submit():
        session['name'] = form.name.data         
        return redirect(url_for('index'))
    return render_template('index.html', form=form, name=session.get('name')
'''

---

类型名| Python类型 |说　　明
---|---|---
Integer | int | 普通整数，一般是32位 
SmallInteger | int | 取值范围小的整数，一般是16位
BigInteger | int 或 long | 不限制精度的整数 
Float | float | 浮点数 
Numeric | decimal.Decimal | 定点数
String | str | 变长字符串 
Text | str | 变长字符串，对较长或不限长度的字符串做了优化
Unicode | unicode | 变长 Unicode 字符串 
UnicodeText | unicode | 变长Unicode字符串，对较长或不限长度的字符串做了优化
Boolean | bool | 布尔值 
Date | datetime.date | 日期 
Time | datetime.time | 时间 
DateTime | datetime.datetime | 日期和时间 
Interval | datetime.timedelta | 时间间隔
Enum | str | 一组字符串 
PickleType | 任何 Python 对象 | 自动使用 Pickle 序列化 LargeBinary | str | 二进制文件


---


选项名 | 说明
--- | ---
backref | 在关系的另一个模型中添加反向引用
primaryjoin | 明确指定两个模型之间使用的联结条件。只在模棱两可的关系中需要指定 
lazy | 指定如何加载相关记录。可选值有select（首次访问时按需加载）、immediate（源对象加载后就加载）、joined（加载记录，但使用联结）、subquery（立即加载，但使用子查询）， noload（永不加载）和 dynamic（不加载记录，但提供加载记录的查询）
uselist | 如果设为 Fales，不使用列表，而使用标量值 
order_by | 指定关系中记录的排序方式 
secondary | 指定多对多关系中关系表的名字 
secondaryjoin | SQLAlchemy无法自行决定时，指定多对多关系中的二级联结条件


---
在蓝本中定义的路由处于休眠状态，直到蓝本注册到程序上后，路由才真正成为程序 的一部分。使用位于全局作用域中的蓝本时，定义路由的方法几乎和单脚本程序一样。

---
