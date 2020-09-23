---
description: Категории заданий — управление категориями заданий
title: Категории заданий — управление категориями заданий
ms.custom: seo-lt-2019
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql13.ag.job.categories.f1
helpviewer_keywords:
- Job Categories dialog box
ms.assetid: 38276438-40b1-43ce-9aae-6805be6d9332
author: markingmyname
ms.author: maghan
ms.reviewer: ''
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 314318a46e6d93aa71f3715d781cf66379fe0863
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88468641"
---
# <a name="job-categories---manage-job-categories"></a>Категории заданий — управление категориями заданий
[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]

> [!IMPORTANT]  
> В [Управляемом экземпляре Azure SQL](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance) в настоящее время поддерживается большинство функций агента SQL Server (но не все). Подробные сведения см. в статье [Различия в T-SQL между Управляемым экземпляром SQL Azure и SQL Server](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

Диалоговое окно **Категории заданий** используется для добавления или удаления категорий заданий. Встроенные категории заданий удалить невозможно.  
  
## <a name="options"></a>Параметры  
**имя**;  
Имя категории заданий.  
  
**Число заданий в категории**  
Количество заданий, определенных для данной категории.  
  
**Просмотр заданий**  
Открывает диалоговое окно **Свойства** для выбранной категории, содержащее список всех заданий, определенных в настоящий момент для этой категории.  
  
**Добавление**  
Открывает диалоговое окно **Создание категории заданий** для добавления новой категории заданий.  
  
**Удаление**  
Удаляет выбранную категорию заданий. Работает только для категорий заданий, определенных пользователями.  
  
**Обновить**  
Отправляет серверу запрос на текущие данные.  
  
#### <a name="to-access-the-job-categories-dialog-box"></a>Для вызова диалогового окна «Категории заданий»  
  
1.  В **обозревателе объектов**разверните **Агент SQL Server**, щелкните правой кнопкой мыши элемент **Задания**, а затем выберите **Управление категориями заданий**.  
  
