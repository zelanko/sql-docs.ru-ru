---
title: Записные книжки с ядром Python в Azure Data Studio
description: В этом учебнике показано, как создать и запустить записную книжку Python.
ms.topic: tutorial
ms.prod: azure-data-studio
ms.technology: azure-data-studio
author: garyericson
ms.author: garye
ms.reviewer: mikeray, alayu, maghan
ms.custom: ''
ms.date: 07/01/2020
ms.openlocfilehash: 38223789b149f0302005c39a42fdd18eb73ec2f6
ms.sourcegitcommit: e3460309b301a77d0babec032f53de330da001a9
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/24/2020
ms.locfileid: "91136811"
---
# <a name="create-and-run-a-python-notebook"></a>Создание и запуск записной книжки Python

[!INCLUDE[SQL Server 2019](../../includes/applies-to-version/sqlserver2019.md)]

В этом руководстве показано, как создать и запустить записную книжку в Azure Data Studio с помощью ядра Python.

## <a name="prerequisites"></a>Предварительные требования

- [Установленное решение Azure Data Studio](../download-azure-data-studio.md)

## <a name="create-a-notebook"></a>Создание записной книжки

Выполните следующие действия, чтобы создать файл записной книжки в Azure Data Studio:

1. Откройте Azure Data Studio. Если появится запрос на подключение к SQL Server, подключитесь или нажмите кнопку **Отмена**.

1. Выберите **Создать записную книжку** в меню **Файл**.

1. Выберите **Python 3** в качестве значения для параметра **Ядро**. Для параметра **Присоединить к** задано значение localhost.

   :::image type="content" source="media/notebooks-python-kernel/set-kernel-and-attach-to-python.png" alt-text="Задать ядро":::

Вы можете сохранить записную книжку с помощью команды **Сохранить** или **Сохранить как...** в меню **Файл**.

Чтобы открыть записную книжку, можно использовать команду **Открыть файл...** в меню **Файл**, выбрать **Открыть файл** на странице **приветствия** или использовать команду **Файл: открыть** в палитре команд.

## <a name="change-the-python-kernel"></a>Изменение ядра Python

При первом подключении к ядру Python в записной книжке отображается страница **Настройка Python для записных книжек**. Можно выбрать любой из вариантов:

- **Новая установка Python** — установка новой копии Python для Azure Data Studio.
- **Использование существующей установки Python** — указание пути к существующей установке Python для использования в Azure Data Studio.

Чтобы просмотреть расположение и версию активного ядра Python, создайте ячейку кода и выполните следующие команды Python:

```python
import os
import sys
print(sys.version_info)
print(os.path.dirname(sys.executable))
```

Чтобы подключиться к другой установке Python, выполните следующие действия.

1. В меню **Файл** последовательно выберите команды **Настройки** и **Параметры**.
1. Прокрутите страницу до пункта **Конфигурация записной книжки** в разделе **Расширения**.
1. В разделе **Использовать существующую установку Python** снимите флажок "Локальный путь к уже существующей установке Python, используемой записными книжками".
1. Перезапустите Azure Data Studio.

Когда Azure Data Studio запускается и вы подключаетесь к ядру Python, открывается страница **Настройка Python для записных книжек** и можно выбрать создание новой установки Python или указать путь к существующей установке.

## <a name="run-a-code-cell"></a>Выполнение ячейки кода

Можно создать ячейки, содержащие код SQL, который можно запустить на месте, нажав кнопку **Выполнить ячейку** (скругленная черная стрелка) слева от ячейки. После того как выполнение ячейки будет завершено, в записной книжке будут показаны результаты.

Пример:

1. Добавьте новую ячейку кода Python, выбрав команду **+Код** на панели инструментов.

   :::image type="content" source="media/notebooks-python-kernel/notebook-toolbar-python.png" alt-text="Панель инструментов записной книжки":::

1. Скопируйте приведенный ниже пример, вставьте его в ячейку и щелкните **Выполнить ячейку**. Этот пример выполняет простые математические вычисления, а результат отображается ниже.

   ```python
   a = 1
   b = 2
   c = a/b
   print(c)
   ```

   :::image type="content" source="media/notebooks-python-kernel/run-notebook-cell-python.png" alt-text="Запуск ячейки записной книжки":::

## <a name="next-steps"></a>Дальнейшие действия

Дополнительные сведения о записных книжках:

- [Расширение Python с помощью Kqlmagic](./notebooks-kqlmagic.md)
- [Использование записных книжек в Azure Data Studio](./notebooks-guidance.md)
- [Создание и запуск записной книжки SQL Server](./notebooks-sql-kernel.md)
