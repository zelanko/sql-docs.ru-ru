---
title: MSSQLSERVER_2519 | Документация Майкрософт
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: language-reference
helpviewer_keywords:
- 2519 (Database Engine error)
ms.assetid: 8dc6ad98-5db8-4c88-8dea-6d455e63b839
caps.latest.revision: 18
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: a8998e454d58c1daa8f099f31d77529f54204631
ms.sourcegitcommit: ee661730fb695774b9c483c3dd0a6c314e17ddf8
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/19/2018
---
# <a name="mssqlserver2519"></a>MSSQLSERVER_2519
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
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
[MSSQLSERVER_2518](~/relational-databases/errors-events/mssqlserver-2518-database-engine-error.md)  
  
