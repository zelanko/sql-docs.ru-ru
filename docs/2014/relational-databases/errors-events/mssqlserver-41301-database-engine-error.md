---
title: MSSQLSERVER_41301 | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 41301 (Database Engine error)
ms.assetid: c6127e1e-2846-4ee9-bc42-2d896ea9730e
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: cb7ce5f35232dca89650079cec9d26151882277d
ms.sourcegitcommit: b57d98e9b2444348f95c83a24b8eea0e6c9da58d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/21/2020
ms.locfileid: "86551479"
---
# <a name="mssqlserver_41301"></a>MSSQLSERVER_41301
    
## <a name="details"></a>Сведения  
  
|attribute|Значение|  
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
 Не выполняйте никаких действий в ходе транзакции. Вызовите ROLLBACK TRAN для отката транзакции. Дополнительные сведения см. в разделе [In-Memory OLTP (оптимизация в памяти)](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md).  
  
## <a name="see-also"></a>См. также:  
 [Включение и отключение групп доступности AlwaysOn (SQL Server)](../../database-engine/availability-groups/windows/enable-and-disable-always-on-availability-groups-sql-server.md)  
  
  
