---
title: MSSQLSERVER_2518 | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 2518 (Database Engine error)
ms.assetid: 54a13abc-4c33-43f0-b55d-e2e74a1381c8
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: df810e28070c797cb24aa3faa308b5419c877139
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62914703"
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
|Текст сообщения|Объект с Идентификатором O_ID (объект «O_NAME»): Вычисляемые столбцы и определяемые пользователем типы нельзя проверить для данного объекта из-за отключения общеязыковой среды выполнения (CLR).|  
  
## <a name="explanation"></a>Объяснение  
 Это информационное сообщение указывает, что обработчик запросов не смог обеспечить команду DBCC внутренним объектом, с помощью которого можно оценить вычисляемые столбцы и определяемые пользователем типы среды CLR. Ошибка произошла, потому что одному из столбцов требовалась среда CLR, но она была отключена. Внутренний объект охватывает все столбцы. Следовательно, невозможность вычислить один столбец препятствует созданию внутреннего объекта. Это означает, что вычисляемые столбцы не будут проверены командой DBCC на корректность и согласованность индексов и базовых таблиц.  
  
## <a name="user-action"></a>Действие пользователя  
 Включите CLR и повторите инструкцию DBCC.  
  
## <a name="see-also"></a>См. также  
 [Включение интеграции со средой CLR](../clr-integration/clr-integration-enabling.md)  
  
  
