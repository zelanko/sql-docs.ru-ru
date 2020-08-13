---
title: Окно команд
description: Узнайте, как использовать командное окно отладчика Transact-SQL для выполнения команд отладки и изменения для отлаживаемого кода.
titleSuffix: T-SQL debugger
ms.prod: sql
ms.technology: scripting
ms.topic: conceptual
helpviewer_keywords:
- Command Window [Transact-SQL]
ms.assetid: e567ebf9-0793-451b-92c7-26193a02d9da
author: markingmyname
ms.author: maghan
ms.reviewer: ''
ms.custom: seo-lt-2019
ms.date: 12/04/2019
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 3e9a1e432de7b9bb0871ffc094f7d37cd1709aff
ms.sourcegitcommit: 216f377451e53874718ae1645a2611cdb198808a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/28/2020
ms.locfileid: "87248068"
---
# <a name="transact-sql-debugger---command-window"></a>Отладчик Transact-SQL, командное окно

 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

**Окно команд** используется для запуска таких команд, как команды отладки и изменения, для кода, отлаживаемого в настоящее время в окне редактора запросов компонента [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]. Чтобы иметь возможность использовать **Окно команд**, необходимо находиться в режиме отладки. Отладчик [!INCLUDE[tsql](../../includes/tsql-md.md)] поддерживает многие из команд, которые также поддерживаются средой в окне [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] **Команда**. Дополнительные сведения см. в разделе [Окно команд среды Visual Studio](https://go.microsoft.com/fwlink/?LinkId=112007).  

[!INCLUDE[ssms-old-versions](../../includes/ssms-old-versions.md)]

## <a name="task-list"></a>Список задач

**Доступ к окну команд**

- В меню **Отладка** выберите команду **Начать отладку**.

**Вывод значения переменной**

- В окне **CommandWindow** введите **Debug.Print \<VariableName>** и нажмите клавишу ВВОД.

**Получение сведений о текущем потоке**

- В окне **CommandWindow**введите **Debug.ListThread**и нажмите клавишу ВВОД.

**Добавление переменной в окно «Быстрая проверка»**

- В окне **CommandWindow** введите **Debug.QuickWatch \<VariableName>** и нажмите клавишу ВВОД.

## <a name="see-also"></a>См. также:

[Отладчик Transact-SQL](../../relational-databases/scripting/transact-sql-debugger.md)
