---
title: Использование функций каталога | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 263df9986df0297c8bf1afdb35d70841835cef4d
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "62667382"
---
# <a name="using-catalog-functions"></a>Использование функций каталога
  Все базы данных имеют структуру, содержащую данные, хранящиеся в базе данных. Определение этой структуры вместе с другими сведениями, например разрешениями, хранится в каталоге (реализованном как набор системных таблиц), который называют словарем данных.  
  
 Драйвер [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ODBC для собственного клиента позволяет приложению определить структуру базы данных с помощью вызовов функций каталога ODBC. Функции каталога возвращают сведения в результирующих наборах и реализуются с помощью запросов хранимых процедур каталога к системным таблицам этого каталога. Например, приложение может запросить результирующий набор, содержащий сведения о всех таблицах в системе или всех столбцах в определенной таблице. Стандартные функции каталога ODBC используются для получения сведений о каталоге из [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], к которому подключено приложение.  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] поддерживает распределенные запросы, в которых доступ к нескольким разнородным источникам данных OLE DB осуществляется одним запросом. Одним из методов доступа к удаленному источнику данных OLE DB является определение источника данных как связанного сервера. Это можно сделать с помощью [sp_addlinkedserver](/sql/relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql). После определения связанного сервера на объекты этого сервера могут ссылаться инструкции Transact-SQL, используя четырехкомпонентное имя:  
  
 *linked_server_name. catalog. Schema. object_name*.  
  
 Драйвер ODBC для собственного клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] поддерживает две зависящие от драйвера функции, помогающие получить сведения о каталоге от связанных серверов.  
  
-   **SQLLinkedServers**  
  
     Возвращает список связанных серверов, определенных на локальном сервере.  
  
-   **SQLLinkedCatalogs**  
  
     Возвращает список каталогов, содержащихся на связанном сервере.  
  
 После создания имени связанного сервера и каталога драйвер ODBC для [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] собственного клиента поддерживает получение сведений из каталога, используя имя из двух частей _linked_server_name_**.** _Каталог_ для *CatalogName* для следующих функций каталога ODBC:  
  
-   **SQLColumnPrivileges**  
  
-   **SQLColumns**  
  
-   **SQLPrimaryKeys**  
  
-   **SQLStatistics**  
  
-   **SQLTablePrivileges**  
  
-   **SQLTables**  
  
 Linked_server_name из двух частей _linked_server_name_**.** _Каталог_ также поддерживается для *фккаталогнаме* и *пккаталогнаме* на [SQLForeignKeys](../../native-client-odbc-api/sqlforeignkeys.md).  
  
 Использование SQLLinkedServers и SQLLinkedCatalogs требует следующих файлов.  
  
-   sqlncli.h  
  
     Включает прототипы функций и определения констант для функций каталога связанного сервера. Файл sqlncli.h необходимо включить в приложение ODBC; при компиляции приложения он должен находиться в пути поиска включаемых файлов.  
  
-   sqlncli11.lib  
  
     Должна находиться в пути к библиотекам компоновщика и определена как файл для связывания. Файл sqlncli11.lib поставляется вместе с драйвером ODBC [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client.  
  
-   sqlncli11.dll  
  
     Необходима во время выполнения. Файл sqlncli11.dll поставляется вместе с драйвером ODBC [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client.  
  
## <a name="see-also"></a>См. также  
 [SQL Server Native Client &#40;ODBC&#41;](sql-server-native-client-odbc.md)   
 [SQLColumnPrivileges](../../native-client-odbc-api/sqlcolumnprivileges.md)   
 [SQLColumns](../../native-client-odbc-api/sqlcolumns.md)   
 [SQLPrimaryKeys](../../native-client-odbc-api/sqlprimarykeys.md)   
 [SQLTablePrivileges](../../native-client-odbc-api/sqltableprivileges.md)   
 [SQLTables](../../native-client-odbc-api/sqltables.md)   
 [SQLStatistics](../../statistics/statistics.md)  
  
  
