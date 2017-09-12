### Session-2: Roles and include

This part will introduce the usage of **Roles and Include**

#### 文件目录讲解

- 如果 roles/x/tasks/main.yml 存在, 其中列出的 tasks 将被添加到 play 中
- 如果 roles/x/handlers/main.yml 存在, 其中列出的 handlers 将被添加到 play 中
- 如果 roles/x/vars/main.yml 存在, 其中列出的 variables 将被添加到 play 中
- 如果 roles/x/meta/main.yml 存在, 其中列出的 “角色依赖” 将被添加到 roles 列表中 (1.3 and later)
- 所有 copy tasks 可以引用 roles/x/files/ 中的文件，不需要指明文件的路径。
- 所有 script tasks 可以引用 roles/x/files/ 中的脚本，不需要指明文件的路径。
- 所有 template tasks 可以引用 roles/x/templates/ 中的文件，不需要指明文件的路径。
- 所有 include tasks 可以引用 roles/x/tasks/ 中的文件，不需要指明文件的路径。

#### site-*.yml讲解
- site-1.yml: roles的基本用法，include基本用法
- site-2.yml: 定义某些task，在roles之前以及之后执行
- site-3.yml: 角色默认变量，要创建默认变量，只需在 roles 目录下添加 defaults/main.yml 文件。这些变量在所有可用变量中拥有最低优先级
- site-4.yml: 角色依赖，使你可以自动地将其他 roles 拉取到现在使用的 role 中。角色依赖保存在 roles 目录下的 meta/main.yml 文件中。角色依赖总是在role之前执行。默认情况下，作为 “角色依赖” 被添加的 role 只能被添加一次，如果另一个 role 将一个相同的角色列为 “角色依赖” 的对象，它不会被重复执行。但这种默认的行为可被修改，通过添加 allow_duplicates: yes 到 meta/main.yml 文件中

#### Usage

```bash
ansible-playbook site-*.yml -v
```