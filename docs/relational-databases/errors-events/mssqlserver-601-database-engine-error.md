---
title: MSSQLSERVER_601 | Документация Майкрософт
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
f1_keywords:
- "601"
helpviewer_keywords:
- 601 (Database Engine error)
ms.assetid: 2039cc0a-9a43-4369-a04a-935e384388b6
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: a1c516a70788d16fc4c80e5ed0b9f0277eccf020
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85728351"
---
# <a name="mssqlserver_601"></a>MSSQLSERVER_601
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>Сведения  
  
| attribute | Значение |  
| :-------- | :---- |  
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
[MSSQLSERVER_605](../../relational-databases/errors-events/mssqlserver-605-database-engine-error.md)  
[Табличные указания (Transact-SQL)](~/t-sql/queries/hints-transact-sql-table.md)  
[SELECT (Transact-SQL)](~/t-sql/queries/select-transact-sql.md)  
[SET TRANSACTION ISOLATION LEVEL (Transact-SQL)](~/t-sql/statements/set-transaction-isolation-level-transact-sql.md)  
  
