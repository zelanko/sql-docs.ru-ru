---
title: MSSQLSERVER_2518 | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- 2518 (Database Engine error)
ms.assetid: 54a13abc-4c33-43f0-b55d-e2e74a1381c8
caps.latest.revision: 19
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: f40eb8fe404479f5a2bcd68881aec4b2b2d84613
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36100418"
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
  
## <a name="see-also"></a>См. также  
 [Включение интеграции со средой CLR](../clr-integration/clr-integration-enabling.md)  
  
  