---
title: MSSQLSERVER_2516 | Документация Майкрософт
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: errors-events
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
helpviewer_keywords:
- 2516 (Database Engine error)
ms.assetid: 79ed14b5-f53c-40c6-8334-8a083f732207
caps.latest.revision: 19
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: ba0df2fc4cd14e46ac5b4bee465f2db72f8ff282
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="mssqlserver2516"></a>MSSQLSERVER_2516
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
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
  
