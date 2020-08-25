---
title: Записные книжки с ядром SQL в Azure Data Studio
description: В этом руководстве показано, как создать и запустить записную книжку SQL Server.
author: markingmyname
ms.author: maghan
ms.reviewer: mikeray, alayu
ms.topic: tutorial
ms.prod: azure-data-studio
ms.technology: azure-data-studio
ms.custom: ''
ms.date: 07/01/2020
ms.openlocfilehash: 022950fa27887618f16e5569ffe3370c069ea71c
ms.sourcegitcommit: dc8a30a4a27e15fc6671ca2674da9b7c637ec255
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/21/2020
ms.locfileid: "88745864"
---
# <a name="create-and-run-a-sql-server-notebook"></a>Создание и запуск записной книжки SQL Server

[!INCLUDE[SQL Server 2019](../includes/applies-to-version/sqlserver2019.md)]

В этом руководстве показано, как создать и запустить записную книжку в Azure Data Studio с помощью SQL Server.

## <a name="prerequisites"></a>Предварительные требования

- [Установленное решение Azure Data Studio](download-azure-data-studio.md)
- Установленное решение SQL Server
  - [Windows](../database-engine/install-windows/install-sql-server.md)
  - [Linux](../linux/sql-server-linux-setup.md)

## <a name="create-a--notebook"></a>Создание записной книжки

Выполните следующие действия, чтобы создать файл записной книжки в Azure Data Studio:

1. В Azure Data Studio подключитесь к своему SQL Server.

1. Выберите раздел **Подключения** в окне **Серверы**. Затем выберите **Создать записную книжку**.

   ![Открытие записной книжки](media/notebook-tutorial/azure-data-studio-open-notebook.png)

1. Дождитесь, пока будет заполнено поле **Ядро** и задан целевой контекст (**Присоединить к**). Убедитесь, что для параметра **Ядро** задано **SQL**, и укажите **Присоединить к** для своего SQL Server (в данном примере *localhost*).

   ![Заполнение полей "Ядро" и "Присоединить к"](media/notebook-tutorial/set-kernel-and-attach-to.png)

Вы можете сохранить записную книжку с помощью команды **Сохранить** или **Сохранить как...** в меню **Файл**. 

Чтобы открыть записную книжку, можно использовать команду **Открыть файл...** в меню **Файл**, выбрать **Открыть файл** на странице **приветствия** или использовать команду **Файл: открыть** в палитре команд.

## <a name="change-the-sql-connection"></a>Изменение подключения SQL Server

Чтобы изменить подключение к SQL Server для записной книжки, сделайте следующее.

1. Выберите меню **Присоединить к** на панели инструментов записной книжки, а затем выберите **Изменить подключение**.

   ![На панели инструментов записной книжки щелкните меню "Присоединить к"](./media/notebook-tutorial/select-attach-to-1.png)

2. Теперь можно выбрать последний сервер, использованный для подключения, или ввести сведения о новом подключении.

   ![Выберите сервер в меню "Присоединить к"](./media/notebook-tutorial/select-attach-to-2.png)

## <a name="run-a-code-cell"></a>Выполнение ячейки кода

Можно создать ячейки, содержащие код SQL, который можно запустить на месте, нажав кнопку **Выполнить ячейку** (скругленная черная стрелка) слева от ячейки. После того как выполнение ячейки будет завершено, в записной книжке будут показаны результаты.

Пример:

1. Добавьте новую ячейку кода, выбрав команду **+Код** на панели инструментов.

   ![Панель инструментов записной книжки](media/notebooks-guidance/notebook-toolbar.png)

1. Скопируйте приведенный ниже пример, вставьте его в ячейку и щелкните **Выполнить ячейку**. В этом примере создается база данных.

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

## <a name="save-the-result"></a>Сохранение результата

При выполнении скрипта, возвращающего результат, этот результат можно сохранить в разных форматах с помощью панели инструментов, отображаемой над результатом.

- Сохранить в формате CSV
- Сохранить в формате Excel
- Сохранить в формате JSON
- Сохранить в формате XML

Например, следующий код возвращает результат [PI](../t-sql/functions/pi-transact-sql.md).

```sql
SELECT PI() AS PI;
GO
```

![Запуск ячейки записной книжки](media/notebook-tutorial/run-notebook-cell-2.png)

## <a name="next-steps"></a>Дальнейшие действия

Дополнительные сведения о записных книжках:

- [Использование записных книжек в Azure Data Studio](notebooks-guidance.md)
- [Создание и запуск записной книжки Python](notebooks-tutorial-python-kernel.md)
- [Запуск примера записной книжки с помощью Spark](../big-data-cluster/notebooks-tutorial-spark.md)