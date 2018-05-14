---
title: MSSQLSERVER_2518 | Документация Майкрософт
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
- 2518 (Database Engine error)
ms.assetid: 54a13abc-4c33-43f0-b55d-e2e74a1381c8
caps.latest.revision: 19
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: e1fc65fae6ce1bf6f874fdcac72a3a46217b4332
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2018
---
# <a name="mssqlserver2518"></a>MSSQLSERVER_2518
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|2518|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|DBCC_NO_EXPRESSION_EVAL_CLR_DISABLED|  
|Текст сообщения|Идентификатор объекта O_ID (объект "O_NAME"): Вычисляемые столбцы и определяемые пользователем типы нельзя проверить для данного объекта, поскольку отключена среда CLR.|  
  
## <a name="explanation"></a>Объяснение  
Это информационное сообщение указывает, что обработчик запросов не смог обеспечить команду DBCC внутренним объектом, с помощью которого можно оценить вычисляемые столбцы и определяемые пользователем типы среды CLR. Ошибка произошла, потому что одному из столбцов требовалась среда CLR, но она была отключена. Внутренний объект охватывает все столбцы. Следовательно, невозможность вычислить один столбец препятствует созданию внутреннего объекта. Это означает, что вычисляемые столбцы не будут проверены командой DBCC на корректность и согласованность индексов и базовых таблиц.  
  
## <a name="user-action"></a>Действие пользователя  
Включите CLR и повторите инструкцию DBCC.  
  
## <a name="see-also"></a>См. также:  
[Включение интеграции со средой CLR](~/relational-databases/clr-integration/clr-integration-enabling.md)  
  
