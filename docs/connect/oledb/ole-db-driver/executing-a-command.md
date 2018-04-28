---
title: Выполнение команды | Документы Microsoft
description: Выполнение команды
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: oledb-driver-for-sql-server
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- commands [OLE DB Driver for SQL Server]
- OLE DB, executing commands
- sessions [OLE DB Driver for SQL Server]
- OLE DB extensions for XML
- OLE DB Driver for SQL Server, command execution
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 0ea3bc38c8a209758bcc2f0bd6ab34fa62f5ccd0
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="executing-a-command"></a>Выполнение команды
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  После установления соединения с источником данных потребитель вызывает метод **IDBCreateSession::CreateSession** метод для создания сеанса. Сеанс выступает в роли фабрики для команд, наборов строк и транзакций.  
  
 Для непосредственной работы с отдельными таблицами и индексами потребитель запрашивает **IOpenRowset** интерфейса. **IOpenRowset::OpenRowset** метод открывает и возвращает набор строк, содержащий все строки из одной базовой таблицы или индекса.  
  
 Для выполнения команды (например, SELECT \* FROM Authors), потребитель запрашивает **IDBCreateCommand** интерфейса. Потребитель может вызвать **IDBCreateCommand::CreateCommand** метод, чтобы создать командный объект и запросить **ICommandText** интерфейса. **ICommandText::SetCommandText** метод используется для указания команды, которое должно быть выполнено.  
  
 **Execute** команда используется для выполнения команды. Командой может быть любая инструкция SQL или имя процедуры. Не все команды возвращают объект результирующего набора (набор строк). Такие команды, как SELECT * FROM Authors, возвращают результирующий набор.  
  
## <a name="see-also"></a>См. также  
 [Создание приложения с драйвером OLE DB для SQL Server](../../oledb/ole-db-driver/creating-a-oledb-driver-for-sql-server-application.md)  
  
  
