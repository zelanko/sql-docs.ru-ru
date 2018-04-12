---
title: Встроенная терминала в SQL Operations Studio (preview) | Документы Microsoft
description: Дополнительные сведения о встроенной терминала в SQL Operations Studio (preview).
ms.custom: tools|sos
ms.date: 11/15/2017
ms.prod: sql-non-specified
ms.reviewer: alayu; erickang; sstein
ms.suite: sql
ms.prod_service: sql-tools
ms.component: sos
ms.tgt_pltfrm: ''
ms.topic: article
author: yualan
ms.author: alayu
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: b55e86314dd075b61dac5751b29fc541fdf1e2c4
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="integrated-terminal"></a>Встроенная терминалов

В [!INCLUDE[name-sos](../includes/name-sos-short.md)], можно открыть интеграции терминалов изначально начиная с корневого каталога рабочей области. Это может оказаться удобным, как не нужно переключаться windows или изменяет состояние существующего терминалов, чтобы выполнить задачу быстрого командной строки.

Чтобы открыть терминала:

* Используйте **Ctrl +'** сочетания клавиш с апострофа.
* Используйте **представление** | **интеграции терминалов** команду меню.
* Из **палитры команд** (**Ctrl + Shift + P**), используйте **интеграции терминалов вид: переключение** команды.

![Терминалов](media/integrated-terminal/terminal-screen.png)

> [!NOTE]
> Внешние оболочки можно открыть с помощью обозревателя **откройте командную строку** команда (**открыть в терминале** на Mac или Linux) Если вы предпочитаете работать за пределами [!INCLUDE[name-sos](../includes/name-sos-short.md)].

## <a name="managing-multiple-terminals"></a>Управление несколькими терминалы

Можно создать несколько терминалы открыть другой ячейки и легко перемещаться между ними. Экземпляры терминалов можно добавить, нажав значок «плюс» в верхней правой части **ТЕРМИНАЛОВ** панели или путем запуска **Ctrl + Shift +'** команды. Это создает еще одну запись в раскрывающемся списке, который может использоваться для переключения между ними.

![Несколько терминалы](media/integrated-terminal/terminal-multiple-instances.png)

Удаление терминалов экземпляров, нажав в корзину можно кнопку.

> [!TIP]
> При использовании нескольких терминалы широко можно добавить настраиваемые сочетания клавиш для `focusNext`, `focusPrevious` и `kill` появлялся команды [раздел привязок ключ](#key-bindings) в обеспечении переходов между ними, используя только клавиатуру.

## <a name="configuration"></a>Конфигурация

Оболочки используется по умолчанию используется значение `$SHELL` на macOS PowerShell в Windows 10 и cmd.exe в более ранних версиях Windows и Linux. Они могут переопределяться вручную, задав `terminal.integrated.shell.*` в [параметры](settings.md). Аргументы могут быть переданы терминалов оболочки на Linux с использованием macOS `terminal.integrated.shellArgs.*` параметры.

### <a name="windows"></a>Windows

Правильной настройке оболочка в Windows, является предметом поиск вправо исполняемого файла и обновление параметра. Ниже приведен список общих оболочки исполняемых объектов и их местоположениях по умолчанию.

```json
// 64-bit cmd if available, otherwise 32-bit
"terminal.integrated.shell.windows": "C:\\Windows\\sysnative\\cmd.exe"
// 64-bit PowerShell if available, otherwise 32-bit
"terminal.integrated.shell.windows": "C:\\Windows\\sysnative\\WindowsPowerShell\\v1.0\\powershell.exe"
// Git Bash
"terminal.integrated.shell.windows": "C:\\Program Files\\Git\\bin\\bash.exe"
// Bash on Ubuntu (on Windows)
"terminal.integrated.shell.windows": "C:\\Windows\\sysnative\\bash.exe"
```

> [!NOTE]
> Для использования встроенной терминалов оболочки исполняемый файл должен быть консольное приложение, чтобы `stdin/stdout/stderr` может быть перенаправлен.

> [!TIP]
> Интегрированная оболочка терминалов выполняется с разрешениями [!INCLUDE[name-sos](../includes/name-sos-short.md)]. Если необходимо выполнить команду оболочки с повышенными привилегиями (администратор) или различные разрешения, можно использовать программы платформы, такие как `runas.exe` внутри терминала.

### <a name="shell-arguments"></a>Аргументы оболочки

Аргументы можно передать в консоль при запуске.

Например, чтобы включить выполнение bash как оболочка входа (которая выполняется `.bash_profile`), передайте `-l` аргумента (в двойных кавычках):

```json
// Linux
"terminal.integrated.shellArgs.linux": ["-l"]
```

## <a name="terminal-display-settings"></a>Параметры отображения терминалов

Настройки интеграции терминалов шрифта и высота строки со следующими параметрами:

* `terminal.integrated.fontFamily`
* `terminal.integrated.fontSize`
* `terminal.integrated.lineHeight`

## <a id="key-bindings"></a>Терминалов сочетания клавиш

**Представление: переключить интеграции терминалов** команда привязана к **Ctrl + "** для быстрого переключения панели интеграции терминалов или развернуть.

Ниже приведены сочетания клавиш для быстрого перехода в рамках интеграции терминалов.

Key|Command
---|---
**CTRL + "**|Показать интеграции терминалов
**Ctrl + Shift + "**|Создание нового терминала
**CTRL + стрелка вверх**|Прокрутка вверх
**CTRL + стрелка вниз**|Прокрутите вниз
**CTRL + PAGE UP**|Страница прокрутки вверх
**CTRL + PAGE DOWN**|Прокрутите страницу вниз
**CTRL + Home**|Перейдите к началу
**Ctrl + End**|Прокрутите вниз
**CTRL + K**|Очистить терминала

Другие команды терминала доступны и могут быть привязаны к предпочтительной сочетание клавиш.

Подробные сведения.

* `workbench.action.terminal.focus`: Сосредоточьтесь терминала. Подобно переключения, но основное внимание терминалов вместо спрятать, если она отображается.
* `workbench.action.terminal.focusNext`: Рассматривается далее терминалов экземпляра.
* `workbench.action.terminal.focusPrevious`: Основное внимание предыдущий экземпляр терминалов.
* `workbench.action.terminal.kill`: Удаляет текущий экземпляр терминалов.
* `workbench.action.terminal.runSelectedText`: Запустите выбранный текст в терминалов экземпляре.
* `workbench.action.terminal.runActiveFile`: Запустите активный файл в терминалов экземпляре.

### <a name="run-selected-text"></a>Выполнить выделенный текст

Для использования `runSelectedText` команды, выделите текст в редакторе и выполните команду **терминалов: запустите текста, выделенного в терминале Active** через **палитры команд** (**Ctrl + Shift + P**). Терминал пытается выполнить выделенный текст:

![Выполнить выделенный текст](media/integrated-terminal/terminal_run_selected.png)

Если никакой текст не выбран в активном редакторе, строки, в которой находится курсор запускается в окне терминала.

### <a name="copy--paste"></a>Копирование и вставка

Сочетания клавиш для копирования и вставки по выполните стандартов платформы.

* Linux — **Ctrl + Shift + C** и **Ctrl + Shift + V**
* MAC: **Cmd + C** и **Cmd + V**
* Windows: **Ctrl + C** и **Ctrl + V**

### <a name="find"></a>Найти

Встроенная терминалов имеет простой поиск функции, которые могут запускаться с **Ctrl + F**.

Если вы хотите **Ctrl + F** для перехода к оболочке вместо запуска найти мини-приложения на Windows и Linux, необходимо удалить привязку keybinding следующим образом:

```js
{ "key": "ctrl+f", "command": "-workbench.action.terminal.focusFindWidget",
                      "when": "terminalFocus" },
```

### <a name="rename-terminal-sessions"></a>Переименование сеансах терминалов

Теперь возможно переименование интеграции сеансам терминалов с помощью **терминалов: переименование** (`workbench.action.terminal.rename`) команды. Новое имя отображается в терминалов выбора раскрывающегося списка.

### <a name="forcing-key-bindings-to-pass-through-the-terminal"></a>Форсирование планов сочетания клавиш для передачи данных через терминала

Фокус во время интеграции терминалов, многие сочетания клавиш не будет работать, поскольку нажатия клавиш переданные и занятая терминала сам. `terminal.integrated.commandsToSkipShell` Параметр позволяет обойти эту проблему. Он содержит массив имен команд которого сочетания клавиш оболочкой не будет обработан и обрабатываться по [!INCLUDE[name-sos](../includes/name-sos-short.md)] ключа системы привязки. По умолчанию в нем все терминалов сочетания клавиш, кроме select некоторые часто используемые сочетания клавиш.

