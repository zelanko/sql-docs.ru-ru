---
title: MSSQLSERVER_2519 | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 2519 (Database Engine error)
ms.assetid: 8dc6ad98-5db8-4c88-8dea-6d455e63b839
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: ec6663028f2c0e133996053a31acfc0e04b49738
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "62914683"
---
# <a name="mssqlserver_2519"></a>MSSQLSERVER_2519
    
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|2519|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|DBCC_NO_EXPRESSION_EVALUATOR|  
|Текст сообщения|Вычисляемые столбцы и определяемые пользователем типы нельзя проверить для объекта с идентификатором O_ID (объект «O_NAME»), поскольку нельзя инициализировать внутреннее средство оценки выражений.|  
  
## <a name="explanation"></a>Объяснение  
 Это информационное сообщение указывает на то, что обработчик запросов не может предоставить для DBCC внутренний объект, который позволил бы оценить значения вычисляемых столбцов и определяемых пользователем типов среды CLR. Это означает, что не будет проверяться правильность вычисляемых столбцов и определяемых пользователем типов CLR, и они не будут использоваться при проверке командой DBCC согласованности между индексами и базовыми таблицами.  
  
## <a name="user-action"></a>Действие пользователя  
 None  
  
## <a name="see-also"></a>См. также:  
 [MSSQLSERVER_2518](mssqlserver-2518-database-engine-error.md)  
  
  
