---
description: MSSQLSERVER_1406
title: MSSQLSERVER_1406 | Документация Майкрософт
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 1406 (Database Engine error)
ms.assetid: 915f97de-9b74-41f8-8bd5-b2d061416718
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 45c5889a0f79757ccd2ae4de74cccc1eed8846f4
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88334780"
---
# <a name="mssqlserver_1406"></a>MSSQLSERVER_1406
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>Сведения  
  
| attribute | Значение |  
| :-------- | :---- |  
|Название продукта|SQL Server|  
|Идентификатор события|1406|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|DBM_BADSTATEFORFORCESERVICE|  
|Текст сообщения|Не удалось безопасно принудительно запустить службу. Отключите зеркальное отображение и восстановите базу данных «%.*ls», чтобы получить доступ.|  
  
## <a name="explanation"></a>Объяснение  
Компоненту [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] не удается принудительно запустить службу, так как состояние зеркального отображения не гарантирует, что процесс принудительного запуска службы будет выполнен правильно.  
  
## <a name="user-action"></a>Действие пользователя  
Отключите зеркальное отображение базы данных. После этого можно восстановить зеркальную базу данных, чтобы получить к ней доступ.  
  
## <a name="see-also"></a>См. также:  
[Принудительный запуск службы в сеансе зеркального отображения базы данных (Transact-SQL)](~/database-engine/database-mirroring/force-service-in-a-database-mirroring-session-transact-sql.md)  
[Удаление зеркального отображения базы данных (SQL Server)](~/database-engine/database-mirroring/removing-database-mirroring-sql-server.md)  
  
