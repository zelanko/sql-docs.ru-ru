---
title: Категория событий TransactionLog | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- SQL Server event classes, Transactions event category
- event classes [SQL Server], Transactions event category
- Transactions event category [SQL Server]
ms.assetid: bfc75c5b-7115-49d8-9148-a0c84ee66a9a
caps.latest.revision: 27
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 0322fd84cf708b8310b7ec6e1483ae24d998617e
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37166965"
---
# <a name="transactions-event-category"></a>Категория событий Transactions
  Классы событий **Transactions** могут использоваться для наблюдения за состоянием транзакций. Имена классов событий с префиксом **TM:** используются для отслеживания операций, связанных с транзакциями и передающихся через интерфейс управления транзакциями.  
  
## <a name="in-this-section"></a>в этом разделе  
  
|Раздел|Описание|  
|-----------|-----------------|  
|[Класс событий DTCTransaction](dtctransaction-event-class.md)|Отслеживает транзакции, управляемые координатором распределенных транзакций ( [!INCLUDE[msCoName](../../includes/msconame-md.md)] ) (MS DTC). Эти транзакции распределяются между двумя или более экземплярами компонента [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)].|  
|[Класс событий SQLTransaction](sqltransaction-event-class.md)|Отслеживает инструкции [!INCLUDE[tsql](../../includes/tsql-md.md)] BEGIN TRAN, COMMIT TRAN, SAVE TRAN и ROLLBACK TRAN.|  
|[Класс событий TM: Begin Tran Completed](tm-begin-tran-completed-event-class.md)|Указывает, что запрос BEGIN TRANSACTION завершен.|  
|[Класс событий TM: Begin Tran Starting](tm-begin-tran-starting-event-class.md)|Указывает, что запрос BEGIN TRANSACTION начался.|  
|[Класс событий TM: Commit Tran Completed](tm-commit-tran-completed-event-class.md)|Указывает, что запрос COMMIT TRANSACTION завершен.|  
|[Класс событий TM: Commit Tran Starting](tm-commit-tran-starting-event-class.md)|Указывает, что запрос COMMIT TRANSACTION начался.|  
|[Класс событий TM: Promote Tran Completed](tm-promote-tran-completed-event-class.md)|Указывает, что запрос PROMOTE TRANSACTION завершен.|  
|[Класс событий TM: Promote Tran Starting](tm-promote-tran-starting-event-class.md)|Указывает, что запрос PROMOTE TRANSACTION начался.|  
|[Класс событий TM: Rollback Tran Completed](tm-rollback-tran-completed-event-class.md)|Указывает, что запрос ROLLBACK TRANSACTION завершен.|  
|[Класс событий TM: Rollback Tran Starting](tm-rollback-tran-starting-event-class.md)|Указывает, что запрос ROLLBACK TRANSACTION начался.|  
|[Класс событий TM: Save Tran Completed](tm-save-tran-completed-event-class.md)|Указывает, что запрос SAVE TRANSACTION завершен.|  
|[Класс событий TM: Save Tran Starting](tm-save-tran-starting-event-class.md)|Указывает, что запрос SAVE TRANSACTION начался.|  
|[Класс событий TransactionLog](transactionlog-event-class.md)|Отслеживает, когда записи о транзакциях появляются в журнале транзакций базы данных.|  
  
  
