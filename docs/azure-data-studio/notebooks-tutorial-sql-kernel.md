---
title: Записные книжки с ядром SQL в Azure Data Studio
description: В этом руководстве показано, как создать и запустить записную книжку SQL Server.
author: markingmyname
ms.author: maghan
ms.reviewer: mikeray, alayu
ms.topic: tutorial
ms.prod: azure-data-studio
ms.technology: ''
ms.custom: ''
ms.date: 03/30/2020
ms.openlocfilehash: 64e5bcfa188707e784d33a6504b120c4ce0ea553
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85735318"
---
# <a name="create-and-run-a-sql-server-notebook"></a>Создание и запуск записной книжки SQL Server

[!INCLUDE[SQL Server 2019](../includes/applies-to-version/sqlserver2019.md)]

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