---
title: "MSSQLSERVER_2518 | Документация Майкрософт"
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords:
- 2518 (Database Engine error)
ms.assetid: 54a13abc-4c33-43f0-b55d-e2e74a1381c8
caps.latest.revision: 19
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Inactive
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: b37286d2e4eff6ee52acacf81e784ea8e554bf59
ms.contentlocale: ru-ru
ms.lasthandoff: 06/22/2017

---
# <a name="mssqlserver2518"></a>MSSQLSERVER_2518
  
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
  

