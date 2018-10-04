---
title: Инструкции SQL, сформированные во время выполнения | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- run time constructed SQL statements [ODBC]
- SQL statements [ODBC], constructing
- SQL statements [ODBC], building at run time
ms.assetid: f6554486-d49c-436a-82e3-4c158d26acd8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 0573851ee93bda4aa33e8645148cf2ee66200bee
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47848102"
---
# <a name="sql-statements-constructed-at-run-time"></a>Инструкции SQL, сформированные во время выполнения
Приложения, которые обычно выполняют специализированный анализ инструкции SQL во время выполнения. Например таблицу может позволить пользователю выбрать столбцы, из которого необходимо извлечь данные:  
  
```  
// SQL_Statements_Constructed_at_Run_Time.cpp  
#include <windows.h>  
#include <stdio.h>  
#include <sqltypes.h>  
  
int main() {  
   SQLCHAR *Statement = 0, *TableName = 0;  
   SQLCHAR **TableNamesArray, **ColumnNamesArray = 0;  
   BOOL *ColumnSelectedArray = 0;  
   BOOL  CommaNeeded;  
   SQLSMALLINT i = 0, NumColumns = 0;  
  
   // Use SQLTables to build a list of tables (TableNamesArray[]). Let the  
   // user select a table and store the selected table in TableName.  
  
   // Use SQLColumns to build a list of the columns in the selected table  
   // (ColumnNamesArray). Set NumColumns to the number of columns in the  
   // table. Let the user select one or more columns and flag these columns  
   // in ColumnSelectedArray[].  
  
   // Build a SELECT statement from the selected columns.  
   CommaNeeded = FALSE;  
   Statement = (SQLCHAR*)malloc(8);  
   strcpy_s((char*)Statement, 8, "SELECT ");  
  
   for (i = 0 ; i = NumColumns ; i++) {  
      if (ColumnSelectedArray[i]) {  
         if (CommaNeeded)  
            strcat_s((char*)Statement, sizeof(Statement), ",");  
         else  
            CommaNeeded = TRUE;  
         strcat_s((char*)Statement, sizeof(Statement), (char*)ColumnNamesArray[i]);  
      }  
   }  
  
   strcat_s((char*)Statement, 15, " FROM ");  
   // strcat_s((char*)Statement, 100, (char*)TableName);  
  
   // Execute the statement . It will be executed once, do not prepare it.  
   // SQLExecDirect(hstmt, Statement, SQL_NTS);  
}  
```  
  
 Другой класс приложений, часто инструкций SQL во время выполнения, сред разработки приложений. Тем не менее инструкции, которые они создания жестко запрограммированы в приложении, которое они создадут, где они обычно оптимизировать их и протестированы.  
  
 Приложения, создания инструкций SQL во время выполнения можно указывать потрясающую гибкость для пользователя. Как видно из предыдущего примера, который еще не поддерживает такие распространенные операции, как **ГДЕ** предложений, **ORDER BY** предложения, или соединения, построение инструкций SQL во время выполнения более сложных чем жесткое программирование инструкции. Кроме того тестирование таких приложений является проблематичным, поскольку их можно создать произвольное число инструкций SQL.  
  
 К недостаткам построение инструкций SQL во время выполнения является то, что занимает гораздо больше времени, чтобы создать инструкцию, чем оператор жестко. К счастью это редко является проблемой. Такие приложения, как правило обработки пользовательского интерфейса и приложение тратит время построение инструкций SQL обычно невелик по сравнению с временем, пользователь тратит ввода критериев.
