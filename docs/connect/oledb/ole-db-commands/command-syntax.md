---
title: Синтаксис команды | Документация Майкрософт
description: Синтаксис команды и хранимые процедуры
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: oledb|ole-db-commands
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- OLE DB Driver for SQL Server, commands
- commands [OLE DB]
- OLE DB Driver for SQL Server, stored procedures
- stored procedures [OLE DB], command syntax
author: pmasl
ms.author: pelopes
manager: craigg
ms.openlocfilehash: 12658166ef66a05bfa18eb6c5c77809e548252ea
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2018
ms.locfileid: "43019230"
---
# <a name="command-syntax"></a>Синтаксис команды
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Драйвер OLE DB для SQL Server распознает синтаксис команды, указанный макросом DBGUID_SQL. Для драйвер OLE DB для SQL Server, описатель указывает, что сочетание ODBC SQL, ISO и [!INCLUDE[tsql](../../../includes/tsql-md.md)] является допустимым синтаксисом. Например, следующая инструкция SQL использует escape-последовательность ODBC SQL, чтобы указать строковую функцию LCASE.  
  
```  
SELECT customerid={fn LCASE(CustomerID)} FROM Customers  
```  
  
 Функция LCASE возвращает строковое выражение, в котором все символы приведены к нижнему регистру. Строковая функция LOWER стандарта ISO выполняет ту же операцию, поэтому следующая инструкция SQL является эквивалентом ISO для представленной выше инструкции ODBC.  
  
```  
SELECT customerid=LOWER(CustomerID) FROM Customers  
```  
  
 Драйвер OLE DB для SQL Server успешно обрабатывает любую форму инструкции при указании в виде текста для команды.  
  
## <a name="stored-procedures"></a>Хранимые процедуры  
 При выполнении хранимой процедуры [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] с помощью команды драйвера OLE DB для SQL Server используйте escape-последовательность ODBC CALL в тексте команды. В этом случае драйвер OLE DB для SQL Server использует механизм удаленного вызова процедуры [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], чтобы оптимизировать обработку команды. Например, следующая инструкция ODBC SQL является более предпочтительным текстом команды, нежели форма [!INCLUDE[tsql](../../../includes/tsql-md.md)].  
  
-   ODBC SQL  
  
    ```  
    {call SalesByCategory('Produce', '1995')}  
    ```  
  
-   Transact-SQL  
  
    ```  
    EXECUTE SalesByCategory 'Produce', '1995'  
    ```  
  
## <a name="see-also"></a>См. также:  
 [Команды](../../oledb/ole-db-commands/commands.md)  
  
  
