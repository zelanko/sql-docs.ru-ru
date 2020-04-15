---
title: Записные книжки с ядром SQL в Azure Data Studio
description: В этом руководстве показано, как создать и запустить записную книжку SQL Server.
author: markingmyname
ms.author: maghan
ms.reviewer: mikeray, alayu
ms.topic: tutorial
ms.prod: sql
ms.technology: azure-data-studio
ms.custom: ''
ms.date: 03/30/2020
ms.openlocfilehash: 80b44b0cd69a3982be87e1fd0d000a6d6393a7c7
ms.sourcegitcommit: 1124b91a3b1a3d30424ae0fec04cfaa4b1f361b6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/01/2020
ms.locfileid: "80531497"
---
# <a name="create-and-run-a-sql-server-notebook"></a>Создание и запуск записной книжки SQL Server

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

В этом руководстве показано, как создать и запустить записную книжку в Azure Data Studio с помощью SQL Server.

## <a name="prerequisites"></a>Предварительные требования

- [Установленное решение Azure Data Studio](download-azure-data-studio.md)
- Установленное решение SQL Server
  - [Windows](../database-engine/install-windows/install-sql-server.md)
  - [Linux](../linux/sql-server-linux-setup.md)

## <a name="new-notebook"></a>Создание записной книжки

Выполните следующие действия, чтобы создать файл записной книжки в Azure Data Studio:

1. В Azure Data Studio подключитесь к своему SQL Server.

2. Выберите раздел **Подключения** в окне **Серверы**. Затем выберите **Создать записную книжку**.

   ![Открытие записной книжки](media/notebook-tutorial/azure-data-studio-open-notebook.png)

3. Дождитесь, пока будет заполнено поле **Ядро** и задан целевой контекст (**Присоединить к**). Убедитесь, что для параметра **Ядро** задано **SQL**, и укажите **Присоединить к** для своего SQL Server (в данном случае *localhost*).

   ![Заполнение полей "Ядро" и "Присоединить к"](media/notebook-tutorial/set-kernel-and-attach-to.png)

## <a name="run-a-notebook-cell"></a>Запуск ячейки записной книжки

Чтобы запустить любую ячейку записной книжки, нажмите расположенную слева от нее кнопку воспроизведения. После того как выполнение ячейки будет завершено, в записной книжке будут показаны результаты.

### <a name="code"></a>Код

Добавьте новую ячейку кода, выбрав команду **+Код** на панели инструментов.

![Панель инструментов записной книжки](media/notebooks-guidance/notebook-toolbar.png)

В этом примере создается база данных.

```sql
USE master
GO

   -- Drop the database if it already exists
IF  EXISTS (
        SELECT name
        FROM sys.databases
        WHERE name = N'TestNotebookDB'
   )
DROP DATABASE TestNotebookDB
GO

-- Create the database
CREATE DATABASE TestNotebookDB
GO
```

   ![Запуск ячейки записной книжки](media/notebook-tutorial/run-notebook-cell.png)

При выполнении скрипта, возвращающего результат, этот результат можно сохранить в разных форматах.

- Сохранить в формате CSV
- Сохранить в формате Excel
- Сохранить в формате JSON
- Сохранить в формате XML

В этом случае мы возвращаем результат в виде числа [Пи](../t-sql/functions/pi-transact-sql.md).

```sql
SELECT PI() AS PI;
GO
```

![Запуск ячейки записной книжки](media/notebook-tutorial/run-notebook-cell-2.png)

### <a name="text"></a>текст

Добавьте новую текстовую ячейку, выбрав команду **+Текст** на панели инструментов.

![Панель инструментов записной книжки](media/notebooks-guidance/notebook-toolbar.png)

Ячейка перейдет в режим правки, и по мере ввода текста с разметкой Markdown вам будет доступна возможность предпросмотра.

![Ячейка с разметкой Markdown](media/notebooks-guidance/notebook-markdown-cell.png)

Щелкните вне текстовой ячейки, чтобы отобразить текст с разметкой Markdown.

![Текст с разметкой Markdown](media/notebooks-guidance/notebook-markdown-preview.png)

## <a name="next-steps"></a>Дальнейшие действия

Дополнительные сведения о записных книжках:

- [Использование записных книжек в SQL Server](notebooks-guidance.md)

- [Как управлять записными книжками в Azure Data Studio](notebooks-manage-sql-server.md)

- [Запуск примера записной книжки с помощью Spark](../big-data-cluster/notebooks-tutorial-spark.md)