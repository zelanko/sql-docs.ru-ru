---
title: упорядочивание заданий
ms.custom: seo-lt-2019
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- job category
- organize jobs
ms.assetid: 629c3e06-f933-483b-8621-280dbb7a7bd1
author: markingmyname
ms.author: maghan
ms.manager: jroth
ms.reviewer: ''
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: a02f50ed88a2883d0149dbbd37df63b27e87dfa4
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/29/2020
ms.locfileid: "75247605"
---
# <a name="organize-jobs"></a>упорядочивание заданий
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

> [!IMPORTANT]  
> Сейчас в [управляемом экземпляре базы данных SQL Azure](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance) поддерживается большинство функций агента SQL Server (но не все). Подробные сведения см. в статье [Различия T-SQL между управляемым экземпляром базы данных SQL Azure и SQL Server](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

Категории заданий помогают упорядочивать их, упрощая их фильтрацию и группирование. Например, все фоновые задания можно поместить в категорию «Обслуживание базы данных». Можно создавать и собственные категории заданий.  
  
> [!WARNING]  
> Многосерверные категории существуют только на главном сервере. На нем по умолчанию имеется только одна категория заданий: [**Без категорий (многосерверный)** ]. Если загружается многосерверное задание, его категория на целевом сервере меняется на **Задания от главного сервера** .  
  
## <a name="related-tasks"></a>Связанные задачи  
  
|||  
|-|-|  
|**Описание**|**Раздел**|  
|Описывает создание категории заданий.|[Создание категории заданий](../../ssms/agent/create-a-job-category.md)|  
|Описывает удаление категории заданий.|[Удаление категории заданий](../../ssms/agent/delete-a-job-category.md)|  
|Описывает назначение задания для категории заданий.|[Назначение задания в категорию заданий](../../ssms/agent/assign-a-job-to-a-job-category.md)|  
|Описывает изменение состава категории заданий.|[Change the Membership of a Job Category](../../ssms/agent/change-the-membership-of-a-job-category.md)|  
|Описывает способы просмотра сведений о категории.|[Просмотр сведений о категории задания](../../ssms/agent/list-job-category-information.md)|  
  
