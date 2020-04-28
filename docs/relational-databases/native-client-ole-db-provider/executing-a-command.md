---
title: Выполнение команды | Документация Майкрософт
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- commands [SQL Server Native Client]
- OLE DB, executing commands
- sessions [SQL Server Native Client]
- OLE DB extensions for XML
- SQL Server Native Client OLE DB provider, command execution
ms.assetid: bb0b3cbf-fe45-46ba-b2ec-c5a39e3c7081
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 88353fa31be9265af5de0e8350aeac5481722351
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "81290201"
---
# <a name="executing-a-command"></a>Выполнение команды
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  После подключения с источнику данных потребитель вызывает метод **IDBCreateSession::CreateSession** для создания сеанса. Сеанс выступает в роли фабрики для команд, наборов строк и транзакций.  
  
 Для непосредственной работы с отдельными таблицами и индексами потребитель запрашивает интерфейс **IOpenRowset**. Метод **IOpenRowset::OpenRowset** открывает и возвращает набор строк, содержащий все строки из единой базовой таблицы или индекса.  
  
 Для выполнения команды (например, SELECT \* FROM Authors) потребитель запрашивает интерфейс **IDBCreateCommand**. Потребитель может вызвать метод **IDBCreateCommand::CreateCommand**, чтобы создать командный объект и запросить интерфейс **ICommandText**. Метод **ICommandText::SetCommandText** используется для указания команды, которую надо выполнить.  
  
 Для выполнения команды используется команда **Execute**. Командой может быть любая инструкция SQL или имя процедуры. Не все команды возвращают объект результирующего набора (набор строк). Такие команды, как SELECT * FROM Authors, возвращают результирующий набор.  
  
## <a name="see-also"></a>См. также:  
 [Создание приложения поставщика OLE DB для собственного клиента SQL Server](../../relational-databases/native-client-ole-db-provider/creating-a-sql-server-native-client-ole-db-provider-application.md)  
  
  
