# ObjectiveCodeStyle

## 编码规范

### 自动Format配置
```
1. Download [clang-format 3.5.2](http://llvm.org/releases/3.5.2/clang+llvm-3.5.2-x86_64-apple-darwin.tar.xz)
2. Copy clang-format into folder `/usr/local/bin/`
3. Edit `~/.profile`, insert a new line `export PATH=/usr/local/bin:$PATH`
4. `. ~/.profile`
5. Copy [pre-commit](https://github.com/augmn/tios/wiki/Content-of-pre-commit) into folder `.gits/hooks/`
6. `chmod +x pre-commit`
7. Change `.clang-format` if you want to change the style.
```

#### 上面步奏已经脚本实现直接使用format_setup.sh初始完成
#### 注意需要先安装wget
#### 在当前目录下执行

```bash
bash format_setup.sh path/to/your/ios/project
```

### 编码格式

[Google Styleguide](https://google.github.io/styleguide/objcguide.xml)

[中文翻译](http://zh-google-styleguide.readthedocs.io/en/latest/google-objc-styleguide/contents/)


#### Swift Style 
1.0 Add the following line in the pre-commit file (unlike the Xcode build phase approach, this uses your locally installed version of SwiftFormat, not a separate copy in your project repository)

```
#!/bin/bash
git diff --diff-filter=d --staged --name-only | grep -e '\(.*\).swift$' | while read line; do
  swiftformat "${line}";
  git add "$line";
done
```

2.0 Enable the hook by typing chmod +x .git/hooks/pre-commit in the terminal
