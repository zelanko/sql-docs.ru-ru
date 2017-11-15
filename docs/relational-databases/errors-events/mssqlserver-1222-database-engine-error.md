---
title: "MSSQLSERVER_1222 | Документация Майкрософт"
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords: 1222 (Database Engine error)
ms.assetid: c5b1c2f4-f591-4cc1-aa17-204636a27f29
caps.latest.revision: "20"
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Inactive
ms.openlocfilehash: 423f504ba458968c98d0bad3da1e78bf0ed01e84
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/09/2017
---
# <a name="mssqlserver1222"></a>MSSQLSERVER_1222
  
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
  
