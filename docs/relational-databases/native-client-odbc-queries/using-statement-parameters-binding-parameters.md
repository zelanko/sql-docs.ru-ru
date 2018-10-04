---
title: Привязка параметров | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, parameters
- parameters [SQL Server Native Client], ODBC
- statements [ODBC], parameters
- binding parameters [SQL Server Native Client]
- parameter markers [ODBC]
- unbound parameter markers
- SQLBindParameter function
- ODBC applications, parameters
- bound parameter markers [SQL Server Native Client]
ms.assetid: d6c69739-8f89-475f-a60a-b2f6c06576e2
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 3927708ae0e9fe00043bc0cb51926d836dd912f5
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47748702"
---
# <a name="using-statement-parameters---binding-parameters"></a>Использование параметров инструкции — привязка параметров
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Каждый маркер параметра в инструкции SQL должен быть сопоставлен переменной в приложении (привязан к ней), прежде чем можно выполнить инструкцию. Это делается путем вызова [SQLBindParameter](../../relational-databases/native-client-odbc-api/sqlbindparameter.md) функции. **SQLBindParameter** описывает переменную программы (адрес, тип данных C и т. д.) к драйверу. Она также определяет маркер параметра, указывая его порядковое значение, а затем описывая характеристики представляемого им объекта SQL (тип данных SQL, точность и т. д.).  
  
 Маркеры параметров могут быть привязаны или повторно привязаны в любое время перед выполнением инструкции. Привязка параметра действует до тех пор, пока не происходит одно из следующих событий.  
  
-   Вызов [SQLFreeStmt](../../relational-databases/native-client-odbc-api/sqlfreestmt.md) с *параметр* параметр в значение SQL_RESET_PARAMS освобождает все параметры, привязанные к дескриптору инструкции.  
  
-   Вызов **SQLBindParameter** с *ParameterNumber* набора порядковый номер маркера параметра автоматически отменяет предыдущую привязку.  
  
 Приложение также может привязать параметры к массивам переменных программы для пакетной обработки инструкции SQL. Существует два типа привязки массивов.  
  
-   Привязка на уровне столбца выполняется, если каждый отдельный параметр привязан к собственному массиву переменных.  
  
     Привязка на уровне столбца указывается путем вызова функции [SQLSetStmtAttr](../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md) с *атрибут* значение SQL_ATTR_PARAM_BIND_TYPE и *ValuePtr* установленным в значение SQL_PARAM_BIND_BY_COLUMN.  
  
-   Привязка на уровне строки выполняется, если все параметры в инструкции SQL привязаны в виде блока к массиву структур, которые содержат отдельные переменные для параметров.  
  
     Привязка на уровне строки указывается путем вызова функции **SQLSetStmtAttr** с *атрибут* значение SQL_ATTR_PARAM_BIND_TYPE и *ValuePtr* равным размеру вместимость структуры переменные программы.  
  
 Когда [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] драйвер ODBC собственного клиента отправляет символ или двоичные строковые параметры на сервер, он дополняет значения до длины, указанной в **SQLBindParameter** *ColumnSize* параметра. Если указано значение 0 в приложении ODBC 2.x *ColumnSize*, драйвер дополняет значение параметра точности типа данных. Точность равна 8000 при соединении с сервером [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и 255 при соединении с предыдущими версиями [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. *ColumnSize* указывается в байтах для столбцов типа variant.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поддерживает определение имен для параметров хранимых процедур. В ODBC 3.5 также появилась поддержка именованных параметров, используемых при вызове хранимых процедур [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Эта поддержка может использоваться для следующих действий.  
  
-   Вызов хранимой процедуры и предоставление значений для подмножества параметров, заданных для хранимой процедуры.  
  
-   Указание параметров в приложении не в той последовательности, в какой они были заданы при создании хранимой процедуры.  
  
 Именованные параметры поддерживаются только в том случае, при использовании [!INCLUDE[tsql](../../includes/tsql-md.md)] **EXECUTE** инструкции или escape-последовательность ODBC CALL для выполнения хранимой процедуры.  
  
 Если **SQL_DESC_NAME** имеет значение для параметра хранимой процедуры, остальные параметры хранимой процедуры в запросе также следует задать **SQL_DESC_NAME**.  Если используются литералы вызовов хранимых процедур, параметры которой имеют **SQL_DESC_NAME** задано, эти литералы должны иметь формат *"имя*=*значение*", где *имя* является именем параметра хранимой процедуры (например, @p1). Дополнительные сведения см. в разделе [привязка параметров по имени (именованные параметры)](http://go.microsoft.com/fwlink/?LinkId=167215).  
  
## <a name="see-also"></a>См. также  
 [Использование параметров инструкции](../../relational-databases/native-client-odbc-queries/using-statement-parameters.md)  
  
  
