---
title: MSSQLSERVER_1406 | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 1406 (Database Engine error)
ms.assetid: 915f97de-9b74-41f8-8bd5-b2d061416718
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 612c39b57682e5b7cfcefd1988e7674f25fb913c
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48141809"
---
# <a name="mssqlserver1406"></a>MSSQLSERVER_1406
    
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|1406|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|DBM_BADSTATEFORFORCESERVICE|  
|Текст сообщения|Не удалось безопасно принудительно запустить службу. Отключите зеркальное отображение и восстановите базу данных «%.*ls», чтобы получить доступ.|  
  
## <a name="explanation"></a>Объяснение  
 Компоненту [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] не удается принудительно запустить службу, так как состояние зеркального отображения не гарантирует, что процесс принудительного запуска службы будет выполнен правильно.  
  
## <a name="user-action"></a>Действие пользователя  
 Отключите зеркальное отображение базы данных. После этого можно восстановить зеркальную базу данных, чтобы получить к ней доступ.  
  
## <a name="see-also"></a>См. также  
 [Принудительный запуск службы в сеансе зеркального отображения базы данных (Transact-SQL)](../../database-engine/database-mirroring/force-service-in-a-database-mirroring-session-transact-sql.md)   
 [Удаление зеркального отображения базы данных (SQL Server)](../../database-engine/database-mirroring/database-mirroring-sql-server.md)  
  
  
