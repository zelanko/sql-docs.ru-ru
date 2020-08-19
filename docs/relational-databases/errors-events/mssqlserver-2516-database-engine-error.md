---
description: MSSQLSERVER_2516
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
ms.openlocfilehash: b62b3d0fcf702b25882c0dee3d312d5339e879f6
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88428786"
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
  
