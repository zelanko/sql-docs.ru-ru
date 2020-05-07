---
title: Записные книжки с ядром Python в Azure Data Studio
description: В этом учебнике показано, как создать и запустить записную книжку Python.
author: garyericson
ms.author: garye
ms.reviewer: mikeray, alayu, maghan
ms.topic: tutorial
ms.prod: sql
ms.technology: azure-data-studio
ms.custom: ''
ms.date: 04/27/2020
ms.openlocfilehash: 8d0666c74f464535d2de08dd44e92c521cfcd73f
ms.sourcegitcommit: 4f4ca7075a73a7a4d7196dcb279c58e15c2daf37
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/28/2020
ms.locfileid: "82196796"
---
# <a name="create-and-run-a-python-notebook"></a>Создание и запуск записной книжки Python

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

В этом руководстве показано, как создать и запустить записную книжку в Azure Data Studio с помощью ядра Python.

## <a name="prerequisites"></a>Предварительные требования

- [Установленное решение Azure Data Studio](download-azure-data-studio.md)

## <a name="new-notebook"></a>Создание записной книжки

Выполните следующие действия, чтобы создать файл записной книжки в Azure Data Studio:

1. Откройте Azure Data Studio. Если появится запрос на подключение к SQL Server, подключитесь или нажмите кнопку **Отмена**.

1. Выберите **Создать записную книжку** в меню **Файл**.

1. Выберите **Python 3** в качестве значения для параметра **Ядро**.

   :::image type="content" source="media/notebook-tutorial-python/set-kernel-and-attach-to-python.png" alt-text="Задать ядро":::

1. Если появится запрос на настройку Python, в пункте **Настроить Python для записных книжек** выберите один из следующих параметров:

   - **Новая установка Python** — установка новой копии Python для Azure Data Studio.
   - **Использование существующей установки Python** — указание пути к существующей установке Python.

## <a name="run-a-notebook-cell"></a>Запуск ячейки записной книжки

Можно создавать ячейки, содержащие код или текст. Можно выполнить ячейку кода на месте, результаты отобразятся в записной книжке после выполнения ячейки. Текстовые ячейки позволяют вставлять код в отформатированную документацию.

### <a name="code"></a>Код

Добавьте новую ячейку кода Python, выбрав команду **+Код** на панели инструментов.

:::image type="content" source="media/notebook-tutorial-python/notebook-toolbar-python.png" alt-text="Панель инструментов записной книжки":::

Этот пример выполняет простые математические вычисления.

```python
a = 1
b = 2
c = a/b
print(c)
```
Запустите ячейку, нажав кнопку воспроизведения слева от ячейки. Результаты отображаются ниже.

:::image type="content" source="media/notebook-tutorial-python/run-notebook-cell-python.png" alt-text="Запуск ячейки записной книжки":::

### <a name="text"></a>текст

Добавьте новую текстовую ячейку, выбрав команду **+Текст** на панели инструментов.

:::image type="content" source="media/notebook-tutorial-python/notebook-toolbar-python-text.png" alt-text="Панель инструментов записной книжки":::

Ячейка перейдет в режим правки, и по мере ввода текста с разметкой Markdown вам будет доступна возможность предпросмотра.

:::image type="content" source="media/notebook-tutorial-python/notebook-markdown-cell-python.png" alt-text="Ячейка с разметкой Markdown":::

Щелкните вне текстовой ячейки, чтобы отобразить только текст с разметкой Markdown.

:::image type="content" source="media/notebook-tutorial-python/notebook-markdown-preview-python.png" alt-text="Текст с разметкой Markdown":::

## <a name="next-steps"></a>Дальнейшие действия

Дополнительные сведения о записных книжках:

- [Использование записных книжек в SQL Server](notebooks-guidance.md)

- [Создание и запуск записной книжки SQL Server](notebooks-tutorial-sql-kernel.md)

- [Как управлять записными книжками в Azure Data Studio](notebooks-manage-sql-server.md)
