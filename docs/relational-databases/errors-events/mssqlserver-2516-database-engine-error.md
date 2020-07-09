---
title: MSSQLSERVER_2516 | Документация Майкрософт
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 2516 (Database Engine error)
ms.assetid: 79ed14b5-f53c-40c6-8334-8a083f732207
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: fd78d5bbe75e544c4b3f1c9cadc4a5656dc72a9c
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85780403"
---
# <a name="mssqlserver_2516"></a>MSSQLSERVER_2516
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>Сведения  
  
| attribute | Значение |  
| :-------- | :---- |  
|Название продукта|SQL Server|  
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
  
