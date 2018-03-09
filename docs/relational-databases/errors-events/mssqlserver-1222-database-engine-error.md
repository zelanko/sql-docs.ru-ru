---
title: "MSSQLSERVER_1222 | Документация Майкрософт"
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: errors-events
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords:
- 1222 (Database Engine error)
ms.assetid: c5b1c2f4-f591-4cc1-aa17-204636a27f29
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 743031212890f81073ac39bb617170cc0e4d218e
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="mssqlserver1222"></a>MSSQLSERVER_1222
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|1222|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|LK_TIMEOUT|  
|Текст сообщения|Истекло время ожидания запроса на блокировку.|  
  
## <a name="explanation"></a>Объяснение  
Другая транзакция удерживает блокировку требуемого ресурса дольше, чем данный запрос может ее ожидать.  
  
## <a name="user-action"></a>Действие пользователя  
Для решения проблемы попробуйте выполнить следующие задачи.  
  
1.  Если это возможно, найдите на требуемом ресурсе транзакцию, удерживающую эту блокировку. Используйте динамические административные представления **sys.dm_os_waiting_tasks** и **sys.dm_tran_locks**.  
  
2.  Если транзакция все еще удерживает блокировку, завершите эту транзакцию, если это адекватно.  
  
3.  Выполните запрос еще раз.  
  
Если данная ошибка возникает часто, измените время ожидания блокировки или вызывающие ошибку транзакции так, чтобы они удерживали блокировку на меньший период времени.  
  
