### Session-3: Variables

This part will introduce the usage of **Variables**


#### site-*.yml讲解
- site-1.yml: 使用Facts获取信息， ansible {{ hostname }} -m setup即可获取到facts变量，具体变量属性见facts.yml。而这些变量可以直接在task中引用
- site-2.yml: 注册变量/变量文件
- site-3.yml: 命令行传递变量 ansible-playbook site-3.yml -v --extra-vars "version=1.0.0" 当然也可也可以传递json数据。--extra-vars '{"pacman":"mrs","ghosts":["inky","pinky","clyde","sue"]}'。 利用@语法传递json文件，--extra-vars "@some_file.json"

#### 变量的优先级
- extra vars (在命令行中使用 -e)优先级最高
- 然后是在inventory中定义的连接变量(比如ansible_ssh_user)
- 接着是大多数的其它变量(命令行转换,play中的变量,included的变量,role中的变量等)
- 然后是在inventory定义的其它变量
- 然后是由系统发现的facts
- 然后是 "role默认变量", 这个是最默认的值,很容易丧失优先权

#### Usage

```bash
ansible-playbook site-*.yml -v
```