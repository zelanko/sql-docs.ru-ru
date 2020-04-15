---
title: Синтаксис команд | Документация Майкрософт
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
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 2d06b72d21dec6e335ef438f0be7838cee4a1231
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304524"
---
# <a name="command-syntax"></a>Синтаксис команды
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Поставщик [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB распознает синтаксис команды, указанный DBGUID_SQL макросом. Для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщика Native Client OLE DB, спецификация указывает, что амальгама ODBC [!INCLUDE[tsql](../../includes/tsql-md.md)] S'L, ISO, и является действительным синтаксисом. Например, следующая инструкция SQL использует escape-последовательность ODBC SQL, чтобы указать строковую функцию LCASE.  
  
```  
SELECT customerid={fn LCASE(CustomerID)} FROM Customers  
```  
  
 Функция LCASE возвращает строковое выражение, в котором все символы приведены к нижнему регистру. Строковая функция LOWER стандарта ISO выполняет ту же операцию, поэтому следующая инструкция SQL является эквивалентом ISO для представленной выше инструкции ODBC.  
  
```  
SELECT customerid=LOWER(CustomerID) FROM Customers  
```  
  
 Поставщик [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB успешно обрабатывает обе формы оператора при указании в качестве текста для команды.  
  
## <a name="stored-procedures"></a>Хранимые процедуры  
 При выполнения сохраненной [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] процедуры [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с помощью команды поставщика Native Client OLE DB используйте последовательность побега ODBC CALL в тексте команды. Затем [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщик Native Client OLE DB использует [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] механизм удаленной процедуры вызова для оптимизации обработки команд. Например, следующая инструкция ODBC SQL является более предпочтительным текстом команды, нежели форма [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
-   ODBC SQL  
  
    ```  
    {call SalesByCategory('Produce', '1995')}  
    ```  
  
-   Transact-SQL  
  
    ```  
    EXECUTE SalesByCategory 'Produce', '1995'  
    ```  
  
## <a name="see-also"></a>См. также:  
 [Команды](../../relational-databases/native-client-ole-db-commands/commands.md)  
  
  
