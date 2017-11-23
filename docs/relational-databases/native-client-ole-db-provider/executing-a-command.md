---
title: "Выполнение команды | Документы Microsoft"
ms.custom: 
ms.date: 03/17/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-ole-db-provider
ms.reviewer: 
ms.suite: sql
ms.technology: docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- commands [SQL Server Native Client]
- OLE DB, executing commands
- sessions [SQL Server Native Client]
- OLE DB extensions for XML
- SQL Server Native Client OLE DB provider, command execution
ms.assetid: bb0b3cbf-fe45-46ba-b2ec-c5a39e3c7081
caps.latest.revision: "40"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 9e37688d49155aa0d3735e1be332e41b0ae79447
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="executing-a-command"></a>Выполнение команды
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  После установления соединения с источником данных потребитель вызывает метод **IDBCreateSession::CreateSession** метод для создания сеанса. Сеанс выступает в роли фабрики для команд, наборов строк и транзакций.  
  
 Для непосредственной работы с отдельными таблицами и индексами потребитель запрашивает **IOpenRowset** интерфейса. **IOpenRowset::OpenRowset** метод открывает и возвращает набор строк, содержащий все строки из одной базовой таблицы или индекса.  
  
 Для выполнения команды (например, SELECT \* FROM Authors), потребитель запрашивает **IDBCreateCommand** интерфейса. Потребитель может вызвать **IDBCreateCommand::CreateCommand** метод, чтобы создать командный объект и запросить **ICommandText** интерфейса. **ICommandText::SetCommandText** метод используется для указания команды, которое должно быть выполнено.  
  
 **Execute** команда используется для выполнения команды. Командой может быть любая инструкция SQL или имя процедуры. Не все команды возвращают объект результирующего набора (набор строк). Такие команды, как SELECT * FROM Authors, возвращают результирующий набор.  
  
## <a name="see-also"></a>См. также:  
 [Создание приложения поставщика OLE DB для SQL Server Native Client](../../relational-databases/native-client-ole-db-provider/creating-a-sql-server-native-client-ole-db-provider-application.md)  
  
  
