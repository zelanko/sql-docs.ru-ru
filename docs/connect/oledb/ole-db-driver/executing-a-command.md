---
title: Выполнение команды | Документация Майкрософт
description: Выполнение команды
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
author: pmasl
ms.author: pelopes
ms.openlocfilehash: f13c9177a74212b849572881f114e503a9530286
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/29/2020
ms.locfileid: "67994988"
---
# <a name="executing-a-command"></a>Выполнение команды
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  После подключения с источнику данных потребитель вызывает метод **IDBCreateSession::CreateSession** для создания сеанса. Сеанс выступает в роли фабрики для команд, наборов строк и транзакций.  
  
 Для непосредственной работы с отдельными таблицами и индексами потребитель запрашивает интерфейс **IOpenRowset**. Метод **IOpenRowset::OpenRowset** открывает и возвращает набор строк, содержащий все строки из единой базовой таблицы или индекса.  
  
 Для выполнения команды (например, SELECT \* FROM Authors) потребитель запрашивает интерфейс **IDBCreateCommand**. Потребитель может вызвать метод **IDBCreateCommand::CreateCommand**, чтобы создать командный объект и запросить интерфейс **ICommandText**. Метод **ICommandText::SetCommandText** используется для указания команды, которую надо выполнить.  
  
 Для выполнения команды используется команда **Execute**. Командой может быть любая инструкция SQL или имя процедуры. Не все команды возвращают объект результирующего набора (набор строк). Такие команды, как SELECT * FROM Authors, возвращают результирующий набор.  
  
## <a name="see-also"></a>См. также:  
 [Создание приложения с драйвером OLE DB для SQL Server](../../oledb/ole-db-driver/creating-a-oledb-driver-for-sql-server-application.md)  
  
  
