---
title: Другие подписчики, отличные от подписчиков SQL Server | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- non-SQL Server Subscribers, other types
ms.assetid: 96b8beb9-38e8-4ce4-97ca-c0f8656b73b4
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 135d317d74a720d51c966ed92f1c305f8c04b838
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "63021949"
---
# <a name="other-non-sql-server-subscribers"></a>Подписчики, отличные от подписчиков SQL Server
  Список[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] подписчиков [!INCLUDE[msCoName](../../../includes/msconame-md.md)], отличных от, поддерживаемых, см. в разделе [подписчики, отличные от SQL Server](non-sql-server-subscribers.md). В данном разделе содержатся сведения о требованиях к драйверам ODBC и поставщикам OLE DB.  
  
## <a name="odbc-driver-requirements"></a>Требования к драйверам ODBC  
 Драйвер ODBC:  
  
-   Должен соответствовать уровню 1 ODBC.  
  
-   Должен быть поточно-защищенным и предназначаться для процессорной архитектуры (Intel или Alpha) и платформы (32-разрядной или 64-разрядной), на которой выполняется распространитель [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
-   Должен поддерживать транзакции.  
  
-   Должен поддерживать язык описания данных (Data Definition Language, DDL).  
  
-   Не может быть доступным только для чтения.  
  
-   Должен поддерживать длинные имена таблиц, такие, как **MSreplication_subscriptions**.  
  
## <a name="replicating-using-ole-db-interfaces"></a>Репликация при помощи интерфейсов OLE DB  
 Поставщики OLE DB должны поддерживать эти объекты для репликации транзакций:  
  
-   Объект **DataSource**  
  
-   Объект **Session**  
  
-   Объект **Command**  
  
-   Объект **набора строк**  
  
-   Объект **Error**  
  
### <a name="datasource-object-interfaces"></a>Интерфейсы объекта DataSource  
 Необходимы следующие интерфейсы для подключения к источнику данных:  
  
-   `IDBInitialize`  
  
-   `IDBCreateSession`  
  
-   `IDBProperties`  
  
 Если поставщик поддерживает интерфейс **IDBInfo** , [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] использует интерфейс для получения сведений, таких, как символ-идентификатор в кавычках, максимальная длина инструкции SQL, а также максимальное число символов в именах таблиц и столбцов.  
  
### <a name="session-object-interfaces"></a>Интерфейсы объекта Session  
 Требуются следующие интерфейсы:  
  
-   **IDBCreateCommand**  
  
-   **Методы**  
  
-   **ITransactionLocal**  
  
-   **IDBSchemaRowset**  
  
### <a name="command-object-interfaces"></a>Интерфейсы объекта Command  
 Требуются следующие интерфейсы:  
  
-   **ICommand**  
  
-   **ICommandProperties**  
  
-   **ICommandText**  
  
-   **ICommandPrepare**  
  
-   **IColumnsInfo**  
  
-   **IAccessor**  
  
-   **ICommandWithParameters**  
  
 **IAccessor** необходим для создания методов доступа к параметрам. Если поставщик поддерживает **иколумнровсет**, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] использует этот интерфейс для определения того, является ли столбец столбцом идентификаторов.  
  
### <a name="rowset-object-interfaces"></a>Интерфейсы объекта Rowset  
 Требуются следующие интерфейсы:  
  
-   **IRowset**  
  
-   **IAccessor**  
  
-   **IColumnsInfo**  
  
 Приложение должно открыть набор строк в реплицированной таблице, которая создается в базе данных подписки. **IColumnsInfo** и **IAccessor** необходимы для доступа к данным в наборе строк.  
  
### <a name="error-object-interfaces"></a>Интерфейсы объекта Error  
 Используйте следующие интерфейсы для управления ошибками:  
  
-   **IErrorRecords**  
  
-   **IErrorInfo**  
  
 Используйте интерфейс **ISQLErrorInfo** , если он поддерживается поставщиком OLE DB.  
  
 Дополнительные сведения о поставщике OLE DB см. в документации, поставляемой с используемым поставщиком OLE DB.  
  
## <a name="see-also"></a>См. также:  
 [Подписчики, не относящиеся к SQL Server](non-sql-server-subscribers.md)  
  
  
