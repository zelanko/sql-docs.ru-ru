---
title: MSSQLSERVER_601 | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- "601"
helpviewer_keywords:
- 601 (Database Engine error)
ms.assetid: 2039cc0a-9a43-4369-a04a-935e384388b6
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 459a983d72a91e628e8cc33636d3abd81998f1d5
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/18/2020
ms.locfileid: "85053819"
---
# <a name="mssqlserver_601"></a>MSSQLSERVER_601
    
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|601|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя||  
|Текст сообщения|Не удалось продолжить просмотр с NOLOCK вследствие перемещения данных.|  
  
## <a name="explanation"></a>Объяснение  
 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] не удается продолжить выполнение запроса, поскольку приложение пытается считать данные, обновленные или удаленные другой транзакцией. Очередь использует указание блокировки NOLOCK или уровень изоляции транзакции READ UNCOMMITTED.  
  
 Как правило, доступ к данным, которые изменяются другой операцией, запрещен из-за наложенной на них блокировки. Однако указание блокировки NOLOCK и уровень изоляции транзакции READ UNCOMMITTED позволили запросу считать данные, заблокированные другой транзакцией. Это называется «грязным» чтением, поскольку таким образом можно считать значения, которые еще не были зафиксированы и могут быть изменены.  
  
## <a name="user-action"></a>Действие пользователя  
 Эта ошибка отменяет запрос. Отправьте запрос повторно или удалите указание блокировки NOLOCK.  
  
## <a name="see-also"></a>См. также:  
 [MSSQLSERVER_605](mssqlserver-605-database-engine-error.md)   
 [Табличные указания (Transact-SQL)](/sql/t-sql/queries/hints-transact-sql-table)   
 [SELECT (Transact-SQL)](/sql/t-sql/queries/select-transact-sql)   
 [SET TRANSACTION ISOLATION LEVEL (Transact-SQL)](/sql/t-sql/statements/set-transaction-isolation-level-transact-sql)  
  
  
