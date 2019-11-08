---
title: Синтаксис команды | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client OLE DB provider, commands
- commands [OLE DB]
- SQL Server Native Client OLE DB provider, stored procedures
- stored procedures [OLE DB], command syntax
ms.assetid: d463d3d7-e5cb-426d-8e92-aa29980356b6
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 88ba95d4664d4ec3247fbd37c4eb33c37410cd6b
ms.sourcegitcommit: 856e42f7d5125d094fa84390bc43048808276b57
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/07/2019
ms.locfileid: "73790666"
---
# <a name="command-syntax"></a>Синтаксис команды
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Поставщик [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB распознает синтаксис команд, указанный в макросе DBGUID_SQL. Для поставщика [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] собственного клиента OLE DB описатель указывает, что амалгам ODBC SQL, ISO и [!INCLUDE[tsql](../../includes/tsql-md.md)] является допустимым синтаксисом. Например, следующая инструкция SQL использует escape-последовательность ODBC SQL, чтобы указать строковую функцию LCASE.  
  
```  
SELECT customerid={fn LCASE(CustomerID)} FROM Customers  
```  
  
 Функция LCASE возвращает строковое выражение, в котором все символы приведены к нижнему регистру. Строковая функция LOWER стандарта ISO выполняет ту же операцию, поэтому следующая инструкция SQL является эквивалентом ISO для представленной выше инструкции ODBC.  
  
```  
SELECT customerid=LOWER(CustomerID) FROM Customers  
```  
  
 Поставщик [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] собственного клиента OLE DB обрабатывает как можно более форму инструкции, если она указана как текст для команды.  
  
## <a name="stored-procedures"></a>Хранимые процедуры  
 При выполнении [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] хранимой процедуры с помощью команды поставщика [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB используйте escape-последовательность вызова ODBC в тексте команды. Поставщик [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] собственного клиента OLE DB использует механизм удаленного вызова процедур [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для оптимизации обработки команд. Например, следующая инструкция ODBC SQL является более предпочтительным текстом команды, нежели форма [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
-   ODBC SQL  
  
    ```  
    {call SalesByCategory('Produce', '1995')}  
    ```  
  
-   Transact-SQL  
  
    ```  
    EXECUTE SalesByCategory 'Produce', '1995'  
    ```  
  
## <a name="see-also"></a>См. также раздел  
 [Команды](../../relational-databases/native-client-ole-db-commands/commands.md)  
  
  
