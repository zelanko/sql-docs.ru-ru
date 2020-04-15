---
title: Использование функций каталога Документы Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- ODBC, functions
- SQLLinkedCatalogs function
- SQL Server Native Client ODBC driver, catalog functions
- SQLLinkedServers function
- catalog functions [ODBC]
- functions [ODBC]
ms.assetid: 7773fb2e-06b5-4c4b-88e9-0ad9132ad273
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 961e44e22ba7db89537f4505a8dec401f9fd69b0
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81303637"
---
# <a name="using-catalog-functions"></a>Использование функций каталога
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Все базы данных имеют структуру, содержащую данные, хранящиеся в базе данных. Определение этой структуры вместе с другими сведениями, например разрешениями, хранится в каталоге (реализованном как набор системных таблиц), который называют словарем данных.  
  
 Драйвер [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC позволяет приложению определять структуру базы данных с помощью вызовов на функции каталога ODBC. Функции каталога возвращают сведения в результирующих наборах и реализуются с помощью запросов хранимых процедур каталога к системным таблицам этого каталога. Например, приложение может запросить результирующий набор, содержащий сведения о всех таблицах в системе или всех столбцах в определенной таблице. Стандартные функции каталога ODBC используются для получения сведений о каталоге из [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], к которому подключено приложение.  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] поддерживает распределенные запросы, в которых доступ к нескольким разнородным источникам данных OLE DB осуществляется одним запросом. Одним из методов доступа к удаленному источнику данных OLE DB является определение источника данных как связанного сервера. Это можно сделать с помощью [sp_addlinkedserver](../../../relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql.md). После определения связанного сервера на объекты этого сервера могут ссылаться инструкции Transact-SQL, используя четырехкомпонентное имя:  
  
 *linked_server_name.catalog.schema.object_name*.  
  
 Драйвер ODBC для собственного клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] поддерживает две зависящие от драйвера функции, помогающие получить сведения о каталоге от связанных серверов.  
  
-   **SQLLinkedServers**  
  
     Возвращает список связанных серверов, определенных на локальном сервере.  
  
-   **SQLLinkedCatalogs**  
  
     Возвращает список каталогов, содержащихся на связанном сервере.  
  
 После того, как у вас есть [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] связанное имя сервера и название каталога, водитель Native Client ODBC поддерживает получение информации из каталога, используя двухраздельное имя _linked_server_name._**.** _Каталог_ для *CatalogName* на следующих функциях каталога ODBC:  
  
-   **SQLColumnPrivileges**  
  
-   **SQLColumns**  
  
-   **SQLPrimaryKeys**  
  
-   **SQLStatistics**  
  
-   **SQLTablePrivileges**  
  
-   **SQLTables**  
  
 Двухсерийный _linked_server_name_**.** _Каталог_ также поддерживается для *FKCatalogName* и *PKCatalogName* на [S'LForeignKeys](../../../relational-databases/native-client-odbc-api/sqlforeignkeys.md).  
  
 Использование SQLLinkedServers и SQLLinkedCatalogs требует следующих файлов.  
  
-   sqlncli.h  
  
     Включает прототипы функций и определения констант для функций каталога связанного сервера. Файл sqlncli.h необходимо включить в приложение ODBC; при компиляции приложения он должен находиться в пути поиска включаемых файлов.  
  
-   sqlncli11.lib  
  
     Должна находиться в пути к библиотекам компоновщика и определена как файл для связывания. Файл sqlncli11.lib поставляется вместе с драйвером ODBC [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client.  
  
-   sqlncli11.dll  
  
     Необходима во время выполнения. Файл sqlncli11.dll поставляется вместе с драйвером ODBC [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client.  
  
## <a name="see-also"></a>См. также:  
 [Родной клиент сервера &#40;ODBC&#41;](../../../relational-databases/native-client/odbc/sql-server-native-client-odbc.md)   
 [СЗЛКолколополИПривилегии](../../../relational-databases/native-client-odbc-api/sqlcolumnprivileges.md)   
 [Sqlcolumns](../../../relational-databases/native-client-odbc-api/sqlcolumns.md)   
 [СЗЛPrimaryKeys](../../../relational-databases/native-client-odbc-api/sqlprimarykeys.md)   
 [СЗЛИБЛПривилегии](../../../relational-databases/native-client-odbc-api/sqltableprivileges.md)   
 [СЗЛТаблицы](../../../relational-databases/native-client-odbc-api/sqltables.md)   
 [SQLStatistics](../../../relational-databases/native-client-odbc-api/sqlstatistics.md)  
  
  
