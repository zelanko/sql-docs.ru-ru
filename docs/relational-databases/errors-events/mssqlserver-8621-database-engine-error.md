---
title: "MSSQLSERVER_8621 | Документация Майкрософт"
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: errors-events
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords:
- 8621 (Database Engine error)
ms.assetid: 67f59865-becd-4999-8bb0-90aedd7effbf
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 052d26f2bdcbfe09e9d71cedd1e99bf85a205805
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="mssqlserver8621"></a>MSSQLSERVER_8621
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|8621|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|OPTIMIZER_STACK_OVERFLOW_ERR|  
|Текст сообщения|При оптимизации запроса обработчик запросов исчерпал пространство стека. Упростите запрос.|  
  
## <a name="explanation"></a>Объяснение  
Наиболее вероятной причиной ошибки является размер расширенного запроса. Расширенный запрос получается при подстановке в основной запрос определений каждого из представлений, вычисляемых столбцов, функций [!INCLUDE[tsql](../../includes/tsql-md.md)] и обобщенных табличных выражений, на которые он ссылается, а также каскадных действий, таких как обновление вторичных индексов, представлений и триггеров.  
  
Наиболее вероятно, что размер запроса велик по определенным измерениям, например числу таблиц, на которые ссылаются определения представления, или очень большому скалярному выражению.  
  
## <a name="user-action"></a>Действие пользователя  
Упростите запрос, разбив его на несколько запросов по наибольшему измерению. Первым делом удалите все необязательные элементы запроса, затем попытайтесь добавить временную таблицу и разбить запрос на две части.  Простого выделения части запроса во вложенный запрос, функцию или обобщенное табличное выражение недостаточно, поскольку они будут объединены компилятором [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
