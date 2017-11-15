---
title: "MSSQLSERVER_2516 | Документация Майкрософт"
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords: 2516 (Database Engine error)
ms.assetid: 79ed14b5-f53c-40c6-8334-8a083f732207
caps.latest.revision: "19"
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Inactive
ms.openlocfilehash: 7893577f260f379e06029a11c6117916709d32cf
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/09/2017
---
# <a name="mssqlserver2516"></a>MSSQLSERVER_2516
  
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|2516|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|DBCC_REPAIR_DIFF_MAP_INVALIDATED|  
|Текст сообщения|Процесс восстановления сделал недействительной битовую карту для базы данных NAME. Цепочка разностного резервного копирования прервана. Перед тем как выполнять разностное резервное копирование, необходимо произвести полное резервное копирование базы данных.|  
  
## <a name="explanation"></a>Объяснение  
Это информационное сообщение возвращается при исправлении ошибки MSSQLEngine_2515.  
  
## <a name="user-action"></a>Действие пользователя  
Создайте полную резервную копию базы данных.  
  
## <a name="see-also"></a>См. также:  
[Создание полной резервной копии базы данных (SQL Server)](~/relational-databases/backup-restore/create-a-full-database-backup-sql-server.md)  
  
