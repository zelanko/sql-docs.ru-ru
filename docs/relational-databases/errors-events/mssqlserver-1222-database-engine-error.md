---
title: MSSQLSERVER_1222 | Документация Майкрософт
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 1222 (Database Engine error)
ms.assetid: c5b1c2f4-f591-4cc1-aa17-204636a27f29
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 7974805b2756ed1b160a254cfda94261a625824c
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "63048961"
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
  
