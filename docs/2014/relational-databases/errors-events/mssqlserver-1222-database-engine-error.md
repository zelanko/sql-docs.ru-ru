---
title: MSSQLSERVER_1222 | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 1222 (Database Engine error)
ms.assetid: c5b1c2f4-f591-4cc1-aa17-204636a27f29
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 01325e8d83a5a7d7b65398f4e0cb981b1fca7540
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "62915903"
---
# <a name="mssqlserver_1222"></a>MSSQLSERVER_1222
    
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
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
  
  
