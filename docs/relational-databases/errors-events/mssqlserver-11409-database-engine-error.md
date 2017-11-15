---
title: "MSSQLSERVER_11409 | Документация Майкрософт"
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords: 11409 (Database Engine error)
ms.assetid: 99b71a1c-a72d-4ca9-9d00-4230c9042ba5
caps.latest.revision: "9"
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Inactive
ms.openlocfilehash: ca191c492eeb5c1d5c717f9a5721c9dcc2a8d0d9
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/09/2017
---
# <a name="mssqlserver11409"></a>MSSQLSERVER_11409
  
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
  
