---
title: MSSQLSERVER_2518 | Документация Майкрософт
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 2518 (Database Engine error)
ms.assetid: 54a13abc-4c33-43f0-b55d-e2e74a1381c8
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 3ff739bf4d3a8e40d398c87b7f350f6adf61e63e
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85780382"
---
# <a name="mssqlserver_2518"></a>MSSQLSERVER_2518
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>Сведения  
  
| attribute | Значение |  
| :-------- | :---- |  
|Название продукта|SQL Server|  
|Идентификатор события|2518|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|DBCC_NO_EXPRESSION_EVAL_CLR_DISABLED|  
|Текст сообщения|Объект с идентификатором O_ID (объект "O_NAME"). Вычисляемые столбцы и определяемые пользователем типы нельзя проверить для данного объекта, поскольку отключена среда CLR.|  
  
## <a name="explanation"></a>Объяснение  
Это информационное сообщение указывает, что обработчик запросов не смог обеспечить команду DBCC внутренним объектом, с помощью которого можно оценить вычисляемые столбцы и определяемые пользователем типы среды CLR. Ошибка произошла, потому что одному из столбцов требовалась среда CLR, но она была отключена. Внутренний объект охватывает все столбцы. Следовательно, невозможность вычислить один столбец препятствует созданию внутреннего объекта. Это означает, что вычисляемые столбцы не будут проверены командой DBCC на корректность и согласованность индексов и базовых таблиц.  
  
## <a name="user-action"></a>Действие пользователя  
Включите CLR и повторите инструкцию DBCC.  
  
## <a name="see-also"></a>См. также:  
[Включение интеграции со средой CLR](~/relational-databases/clr-integration/clr-integration-enabling.md)  
  
