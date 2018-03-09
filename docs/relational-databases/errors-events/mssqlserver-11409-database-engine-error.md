---
title: "MSSQLSERVER_11409 | Документация Майкрософт"
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
- 11409 (Database Engine error)
ms.assetid: 99b71a1c-a72d-4ca9-9d00-4230c9042ba5
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 1c2e15a828cfa41612ed7c2c7eebfbb6eb1aa59d
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="mssqlserver11409"></a>MSSQLSERVER_11409
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|11409|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|ALTERCOL_COLSET_DROP|  
|Текст сообщения|Не удалось удалить набор столбцов "%.*ls" в таблице "%.\*ls", поскольку таблица содержит больше 1025 столбцов.|  
  
## <a name="explanation"></a>Объяснение  
Таблицы могут содержать максимум 1024 столбца, которые не определены как разреженные или вычисляемые. Если наличие разреженных столбцов становится причиной превышения 1024 столбцов в таблице, для таблицы должен быть определен набор столбцов. В указанной таблице больше 1024 столбцов и предпринята попытка удалить набор столбцов.  
  
## <a name="user-action"></a>Действие пользователя  
Текущий состав столбцов в таблице таков, что требует сохранения набора столбцов.  
  
Чтобы удалить набор столбцов, сначала удаляйте из таблицы столбцы, пока их количество не станет меньше или равно 1024 столбцам. После этого можно удалить набор столбцов.  
  
