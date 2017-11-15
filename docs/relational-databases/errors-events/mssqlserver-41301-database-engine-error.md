---
title: "MSSQLSERVER_41301 | Документация Майкрософт"
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords: 41301 (Database Engine error)
ms.assetid: c6127e1e-2846-4ee9-bc42-2d896ea9730e
caps.latest.revision: "10"
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Inactive
ms.openlocfilehash: 7a44ac20040a2a3d6c5c772cf1dfa0008734e06a
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/09/2017
---
# <a name="mssqlserver41301"></a>MSSQLSERVER_41301
  
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|Идентификатор события|41301|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|COMMIT_DEPENDENCY_FAILURE|  
|Текст сообщения|Предыдущая транзакция, от которой зависит текущая транзакция, прервана, текущая транзакция не может быть зафиксирована.|  
  
## <a name="explanation"></a>Объяснение  
В ходе транзакции произошла ошибка зависимости, поэтому транзакция завершается.  
  
Эта ошибка также может быть вызвана слишком большим числом зависимых транзакций. Любые транзакции записи могут иметь только ограниченное число зависимых транзакций. Например, эта ошибка может возникнуть в случае, если слишком большое число транзакций чтения пытаются установить зависимость от транзакции обновления.  
  
## <a name="user-action"></a>Действие пользователя  
Не выполняйте никаких действий в ходе транзакции. Вызовите ROLLBACK TRAN для отката транзакции. Дополнительные сведения см. в разделе [In-Memory OLTP (оптимизация в памяти)](~/relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md).  
  
## <a name="see-also"></a>См. также:  
[Включение и отключение групп доступности AlwaysOn (SQL Server)](~/database-engine/availability-groups/windows/enable-and-disable-always-on-availability-groups-sql-server.md)  
  
