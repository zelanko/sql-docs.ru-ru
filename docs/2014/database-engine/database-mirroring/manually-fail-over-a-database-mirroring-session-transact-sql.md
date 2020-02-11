---
title: Переключение сеанса зеркального отображения базы данных на другой ресурс вручную (язык Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- failover [SQL Server], database mirroring
- manual failover [SQL Server]
- database mirroring [SQL Server], failover
ms.assetid: 36218d61-b5f5-4194-905a-608e0e903db4
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: c10702b169537fc547ff46440883879ee9da417c
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "62754891"
---
# <a name="manually-fail-over-a-database-mirroring-session-transact-sql"></a>Переключение сеанса зеркального отображения базы данных на другой ресурс вручную (язык Transact-SQL)
  Когда зеркальная база данных синхронизирована (то есть база данных находится в состоянии SYNCHRONIZED), владелец базы данных может инициировать отработку отказа на зеркальном сервере вручную. Переход на другой ресурс вручную может быть инициирован только с основного сервера.  
  
### <a name="to-manually-fail-over-a-database-mirroring-session"></a>Отработка отказа в сеансе зеркального отображения базы данных вручную  
  
1.  Подключитесь к основному серверу.  
  
2.  Задайте базу данных **master** в качестве контекста базы данных:  
  
     `USE master;`  
  
3.  Введите следующую инструкцию на основном сервере:  
  
     [ALTER database](/sql/t-sql/statements/alter-database-transact-sql-database-mirroring) *database_name* Set Partner отработка отказа, где *database_name* является зеркальной базой данных.  
  
     В результате роль основного сервера немедленно перейдет к зеркальному серверу.  
  
 На бывшем основном сервере произойдет отключение клиентов базы данных с откатом незавершенных транзакций.  
  
> [!NOTE]  
>  Транзакции, подготовленные с помощью координатора распределенных транзакций [!INCLUDE[msCoName](../../includes/msconame-md.md)] , но еще не зафиксированные на момент отработки отказа, после отработки отказа базы данных будут считаться отмененными.  
  
## <a name="see-also"></a>См. также:  
 [&#41;Transact-SQL для зеркального отображения базы данных ALTER DATABASE &#40;](/sql/t-sql/statements/alter-database-transact-sql-database-mirroring)   
 [Вручную отработка отказа сеанса зеркального отображения базы данных &#40;SQL Server Management Studio&#41;](manually-fail-over-a-database-mirroring-session-sql-server-management-studio.md)   
 [Переключение ролей во время сеанса зеркального отображения базы данных &#40;SQL Server&#41;](role-switching-during-a-database-mirroring-session-sql-server.md)  
  
  
