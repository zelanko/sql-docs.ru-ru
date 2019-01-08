---
title: Категория событий TransactionLog | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- SQL Server event classes, Transactions event category
- event classes [SQL Server], Transactions event category
- Transactions event category [SQL Server]
ms.assetid: bfc75c5b-7115-49d8-9148-a0c84ee66a9a
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 076e68de4dc5d4e25f6cabe6b39ac4a61a05033a
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/03/2018
ms.locfileid: "52801106"
---
# <a name="transactions-event-category"></a>Категория событий Transactions
  Классы событий **Transactions** могут использоваться для наблюдения за состоянием транзакций. Имена классов событий с префиксом **TM:** используются для отслеживания операций, связанных с транзакциями и передающихся через интерфейс управления транзакциями.  
  
## <a name="in-this-section"></a>в этом разделе  
  
|Раздел|Описание|  
|-----------|-----------------|  
|[Класс событий DTCTransaction](dtctransaction-event-class.md)|Отслеживает транзакции, управляемые координатором распределенных транзакций ( [!INCLUDE[msCoName](../../includes/msconame-md.md)] ) (MS DTC). Эти транзакции распределяются между двумя или более экземплярами компонента [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)].|  
|[Класс событий SQLTransaction](sqltransaction-event-class.md)|Отслеживает инструкции [!INCLUDE[tsql](../../includes/tsql-md.md)] BEGIN TRAN, COMMIT TRAN, SAVE TRAN и ROLLBACK TRAN.|  
|[TM: BEGIN Tran Completed, класс событий](tm-begin-tran-completed-event-class.md)|Указывает, что запрос BEGIN TRANSACTION завершен.|  
|[TM: BEGIN Tran Starting, класс событий](tm-begin-tran-starting-event-class.md)|Указывает, что запрос BEGIN TRANSACTION начался.|  
|[TM: COMMIT Tran Completed, класс событий](tm-commit-tran-completed-event-class.md)|Указывает, что запрос COMMIT TRANSACTION завершен.|  
|[TM: COMMIT Tran Starting, класс событий](tm-commit-tran-starting-event-class.md)|Указывает, что запрос COMMIT TRANSACTION начался.|  
|[TM: Promote Tran Completed, класс событий](tm-promote-tran-completed-event-class.md)|Указывает, что запрос PROMOTE TRANSACTION завершен.|  
|[TM: Promote Tran Starting, класс событий](tm-promote-tran-starting-event-class.md)|Указывает, что запрос PROMOTE TRANSACTION начался.|  
|[TM: ROLLBACK Tran Completed, класс событий](tm-rollback-tran-completed-event-class.md)|Указывает, что запрос ROLLBACK TRANSACTION завершен.|  
|[TM: ROLLBACK Tran Starting, класс событий](tm-rollback-tran-starting-event-class.md)|Указывает, что запрос ROLLBACK TRANSACTION начался.|  
|[TM: Save Tran Completed, класс событий](tm-save-tran-completed-event-class.md)|Указывает, что запрос SAVE TRANSACTION завершен.|  
|[TM: Save Tran Starting, класс событий](tm-save-tran-starting-event-class.md)|Указывает, что запрос SAVE TRANSACTION начался.|  
|[Класс событий TransactionLog](transactionlog-event-class.md)|Отслеживает, когда записи о транзакциях появляются в журнале транзакций базы данных.|  
  
  
