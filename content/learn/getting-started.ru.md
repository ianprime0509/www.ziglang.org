---
title: Начало работы
mobile_menu_title: "Начало работы"
toc: true
---

## Конкретный выпуск или ежедневная сборка?
Zig ещё не достиг версии 1.0, и текущий цикл выпуска привязан к новым выпускам LLVM, которые выходят с периодичностью в около 6 месяцев.
На практике, **релизы Zig, как правило, сильно отличаются друг от друга и довольно быстро устаревают, учитывая текущую скорость разработки**.

Вполне можно оценить Zig с помощью одного из выпусков, но если вы решите, что вам нравится Zig и вы
хотите погрузиться глубже, **мы рекомендуем вам перейти на ежедневную сборку**, так как в этом случае
вам будет проще получить помощь: бо́льшая часть сообщества и такие сайты, как
[ziglearn.org](https://ziglearn.org) отслеживают master–ветку по причинам, указанным выше.

Хорошая новость: можно очень легко переключиться от одной версии Zig к другой, или даже иметь несколько версий в системе одновременно, ведь выпуски Zig предоставляются в виде самодостаточных архивов, которые можно разместить в любом месте вашей системы.


## Установка Zig
### Прямая загрузка
Это самый простой способ получить Zig: скачайте пакет Zig для вашей платформы со страницы [Загрузки](/download),
распакуйте его в каталог и добавьте в `PATH`, чтобы иметь возможность вызывать `zig` из любого места.

#### Настройка переменной PATH на Windows
Чтобы настроить переменную PATH на Windows, запустите **один** из нижеперечисленных сценариев PowerShell.
Выберите, хотите ли вы применить эти изменения для всей системы (необходимо запустить PowerShell с правами администратора)
или только для вашего пользователя, и **и обязательно измените сценарий, чтобы он указывал на место, где лежит ваша копия Zig**.
Символ `;` перед `C:` не является опечаткой.

Для всей системы (**администраторский** PowerShell):
```
[Environment]::SetEnvironmentVariable(
   "Path",
   [Environment]::GetEnvironmentVariable("Path", "Machine") + ";C:\ваш-путь-к-распакованному-архиву\zig-windows-x86_64-ваша-версия",
   "Machine"
)
```

PowerShell текущего пользователя:
```
[Environment]::SetEnvironmentVariable(
   "Path",
   [Environment]::GetEnvironmentVariable("Path", "User") + ";C:\ваш-путь-к-распакованному-архиву\zig-windows-x86_64-ваша-версия",
   "User"
)
```
После завершения перезапустите PowerShell.

#### Настройка переменной PATH на Linux, macOS, BSD
Добавьте расположение двоичного файла zig в переменную окружения PATH.

Обычно это делается путём добавления строки экспорта в файлы настроек оболочки (`.profile`, `.zshrc` и т.д.)

```bash
export PATH=$PATH:~/путь/к/zig
```

После завершение перезапустите вашу оболочку или запустите команду `source` с вашим файлом.

### Пакетные менеджеры
#### Windows
**WinGet**
Zig доступен в [WinGet](https://github.com/microsoft/winget-pkgs/tree/master/manifests/z/zig/zig).
```
winget install -e --id zig.zig
```

**Chocolatey**
Zig доступен в [Chocolatey](https://chocolatey.org/packages/zig).
```
choco install zig
```

**Scoop**
Zig доступен в [Scoop](https://scoop.sh/#/apps?q=zig&id=7e124d6047c32d426e4143ab395d863fc9d6d491).
```
scoop install zig
```
Последняя [ночная сборка](https://scoop.sh/#/apps?q=zig&id=921df07e75042de645204262e784a17c2421944c) с master—ветки:
```
scoop bucket add versions
scoop install versions/zig-dev
```

#### macOS

**Homebrew**

Последний выпуск:
```
brew install zig
```

**MacPorts**
```
port install zig
```
#### Linux
Zig также присутствует во многих пакетных менеджерах для Linux. [Здесь](https://github.com/ziglang/zig/wiki/Install-Zig-from-a-Package-Manager)
вы можете найти обновлённый список, но имейте в виду, что некоторые пакеты могут содержать устаревшие версии Zig.

### Сборка из исходного кода
[Здесь](https://github.com/ziglang/zig/wiki/Building-Zig-From-Source) 
вы найдёте больше информации о том, как собрать Zig из исходного кода для Linux, macOS и Windows.

## Рекомендуемые инструменты
### Подсветка синтаксиса и LSP
Все популярные текстовые редакторы поддерживают подсветку синтаксиса для Zig. 
Некоторые предоставляют её, для других же потребуется установка расширения.

Если вам требуется более глубокая интеграция между вашим редактором и Zig,
рассмотрите [zigtools/zls](https://github.com/zigtools/zls).

Для получения подробной информации посетите раздел [Инструменты](../tools/).

## Запуск Hello World
Если вы успешно завершили процесс установки, вы теперь должны иметь возможность вызывать компилятор Zig в вашей оболочке.

Давайте проверим это, создав вашу первую программу Zig!

Перейдите в каталог c вашими проектами и запустите:
```bash
mkdir hello-world
cd hello-world
zig init-exe
```

Это должно вывести:
```
info: Created build.zig
info: Created src/main.zig
info: Next, try `zig build --help` or `zig build run`
```

`zig build run` скомпилирует исполняемый файл и запустит его, и запуск файла выдаст:
```
info: All your codebase are belong to us.
```

Поздравляем, у вас есть работающая установка Zig!

## Следующие шаги
**Ознакомьтесь с другими ресурсами, представленными в разделе [Обучение](../)**, и убедитесь, что вы нашли
документацию для нужной версии Zig (примечание: ежедневные сборки должны использовать документацию `master`),
а также ознакомьтесь с сайтом [ziglearn.org](https://ziglearn.org).

Zig — это молодой проект, и, к сожалению, у нас пока нет возможности создавать обширную документацию и обучающие материалы
по всем вопросам, поэтому вам стоит [присоединиться к одному из существующих сообществ Zig](https://github.com/ziglang/zig/wiki/Community),
чтобы получить помощь в случае затруднений, а также обратите внимание на такие инициативы, как [Zig SHOWTIME](https://zig.show).

Наконец, если вам нравится Zig и вы хотите помочь ускорить разработку, [рассмотрите возможность пожертвования в Zig Software Foundation](../../zsf)
<img src="/heart.svg" style="vertical-align:middle; margin-right: 5px">.
