---
title: Выполнение команды (драйвер OLE DB) | Документация Майкрософт
description: Узнайте, как объект-получатель в OLE DB Driver for SQL Server выполняет команду. Сначала он создает сеанс, а затем получает набор строк и использует команду Execute.
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- commands [OLE DB Driver for SQL Server]
- OLE DB, executing commands
- sessions [OLE DB Driver for SQL Server]
- OLE DB extensions for XML
- OLE DB Driver for SQL Server, command execution
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: f24216ec62b77c56d5d2b18563f64e37fd4b7691
ms.sourcegitcommit: c95f3ef5734dec753de09e07752a5d15884125e2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/25/2020
ms.locfileid: "88861519"
---
# <a name="executing-a-command"></a>Выполнение команды
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  После подключения с источнику данных потребитель вызывает метод **IDBCreateSession::CreateSession** для создания сеанса. Сеанс выступает в роли фабрики для команд, наборов строк и транзакций.  
  
 Для непосредственной работы с отдельными таблицами и индексами потребитель запрашивает интерфейс **IOpenRowset**. Метод **IOpenRowset::OpenRowset** открывает и возвращает набор строк, содержащий все строки из единой базовой таблицы или индекса.  
  
 Для выполнения команды (например, SELECT \* FROM Authors) потребитель запрашивает интерфейс **IDBCreateCommand**. Потребитель может вызвать метод **IDBCreateCommand::CreateCommand**, чтобы создать командный объект и запросить интерфейс **ICommandText**. Метод **ICommandText::SetCommandText** используется для указания команды, которую надо выполнить.  
  
 Для выполнения команды используется команда **Execute**. Командой может быть любая инструкция SQL или имя процедуры. Не все команды возвращают объект результирующего набора (набор строк). Такие команды, как SELECT * FROM Authors, возвращают результирующий набор.  
  
## <a name="see-also"></a>См. также:  
 [Создание приложения с драйвером OLE DB для SQL Server](../../oledb/ole-db-driver/creating-a-oledb-driver-for-sql-server-application.md)  
  
  
