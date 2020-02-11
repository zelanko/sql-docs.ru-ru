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
manager: craigg
ms.openlocfilehash: 9aebe73ac73ee09ed2ba6de9162877d0e70bc7e6
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "62867733"
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
 [Табличные указания &#40;&#41;Transact-SQL](/sql/t-sql/queries/hints-transact-sql-table)   
 [SELECT (Transact-SQL)](/sql/t-sql/queries/select-transact-sql)   
 [SET TRANSACTION ISOLATION LEVEL (Transact-SQL)](/sql/t-sql/statements/set-transaction-isolation-level-transact-sql)  
  
  
