---
title: Синтаксис команды | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
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
manager: craigg
ms.openlocfilehash: 00ab769ee2051edc499d586ab7d5ee1fa47dd854
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48226744"
---
# <a name="command-syntax"></a>Синтаксис команды
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Поставщика OLE DB для собственного клиента распознает синтаксис команды, указанный макросом DBGUID_SQL. Для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщика OLE DB для собственного клиента, описатель указывает, что сочетание ODBC SQL, ISO и [!INCLUDE[tsql](../../includes/tsql-md.md)] является допустимым синтаксисом. Например, следующая инструкция SQL использует escape-последовательность ODBC SQL, чтобы указать строковую функцию LCASE.  
  
```  
SELECT customerid={fn LCASE(CustomerID)} FROM Customers  
```  
  
 Функция LCASE возвращает строковое выражение, в котором все символы приведены к нижнему регистру. Строковая функция LOWER стандарта ISO выполняет ту же операцию, поэтому следующая инструкция SQL является эквивалентом ISO для представленной выше инструкции ODBC.  
  
```  
SELECT customerid=LOWER(CustomerID) FROM Customers  
```  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Поставщика OLE DB для собственного клиента обрабатывает любую форму инструкции успешно при использовании в качестве текста для команды.  
  
## <a name="stored-procedures"></a>Хранимые процедуры  
 При выполнении [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] хранимой процедуры с помощью [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщика OLE DB для собственного клиента команду, используйте escape-последовательность ODBC CALL в тексте команды. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Поставщика OLE DB для собственного клиента затем использует механизм вызова удаленной процедуры [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для оптимизации обработки команд. Например, следующая инструкция ODBC SQL является более предпочтительным текстом команды, нежели форма [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
-   ODBC SQL  
  
    ```  
    {call SalesByCategory('Produce', '1995')}  
    ```  
  
-   Transact-SQL  
  
    ```  
    EXECUTE SalesByCategory 'Produce', '1995'  
    ```  
  
## <a name="see-also"></a>См. также  
 [Команды](commands.md)  
  
  
