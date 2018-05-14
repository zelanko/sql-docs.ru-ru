---
title: MSSQLSERVER_844 | Документация Майкрософт
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: errors-events
ms.reviewer: ''
ms.suite: sql
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: language-reference
helpviewer_keywords:
- 844 (Database Engine error)
ms.assetid: 2060c886-1226-4066-bc0c-de90a1cfb82b
caps.latest.revision: 18
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: f23c78a306e20aaa6537e5295d0eeb2a97055699
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2018
---
# <a name="mssqlserver844"></a>MSSQLSERVER_844
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|844|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|BUFLATCH_TIMEOUT_CONTINUE|  
|Текст сообщения|Истекло время ожидания кратковременной блокировки буфера — тип %d, базовая точка %p, страница %d:%d, stat %#x, идентификатор базы данных: %d, идентификатор единицы распределения: %I64d%ls, задача 0x%p: %d, время ожидания %d, флаги 0x%I64x, задача-владелец 0x%p.  Продолжение ожидания.|  
  
## <a name="explanation"></a>Объяснение  
Процесс ожидает получения кратковременной блокировки. Эта проблема может быть вызвана слишком продолжительной операцией ввода-вывода. Как правило, этот тип ошибки возникает в результате блокирования системных процессов другими задачами. В некоторых случаях эта ошибка может возникать в результате сбоя оборудования.  
  
## <a name="user-action"></a>Действие пользователя  
Для предотвращения этой ошибки попробуйте предпринять следующее.  
  
-   Снизьте рабочую нагрузку.  
  
-   В журнале ошибок или журнале событий проверьте соответствующие сбои операций ввода-вывода. Сбои операций ввода-вывода обычно указывают на неправильную работу диска.  
  
-   В журнале ошибок проверьте наличие невыполненных задач и других критических ошибок.  
  
-   Если критические ошибки встречаются часто, устраните их причину.  
  
Если ошибка продолжает возникать, обратитесь в службу поддержки пользователей корпорации Майкрософт.  
  
