---
title: "Инструкции SQL, сформированные во время выполнения | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- run time constructed SQL statements [ODBC]
- SQL statements [ODBC], constructing
- SQL statements [ODBC], building at run time
ms.assetid: f6554486-d49c-436a-82e3-4c158d26acd8
caps.latest.revision: "6"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 1d9463795697584be0dc1d6f96845cf810857292
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="sql-statements-constructed-at-run-time"></a>Инструкции SQL, сформированные во время выполнения
Приложения, которые часто выполнять нерегламентированный анализ построения инструкций SQL во время выполнения. Например электронной таблицы могут разрешить пользователю выбирать столбцы для извлечения данных из:  
  
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
  
 Другой класс приложений, часто инструкций SQL во время выполнения, среда разработки приложений. Тем не менее на операторы, которые они создания жестко запрограммированы в приложение, которое они строится, где они обычно оптимизированными и протестирован.  
  
 Приложения, создания инструкций SQL во время выполнения можно указывать значительную гибкость для пользователя. Как видно из предыдущего примера, даже не поддерживали таких общих операций, как **ГДЕ** предложений, **ORDER BY** предложений или соединения, создание инструкций SQL во время выполнения намного сложнее, чем жесткое программирование инструкции. Кроме того тестирование таких приложений, затруднительно, поскольку они могут создавать произвольное число инструкций SQL.  
  
 Создание инструкций SQL во время выполнения потенциальных недостаток заключается в том, что он принимает гораздо больше времени для создания инструкции не использовать оператор, жестко. К счастью эта проблема редко. Такие приложения, как правило, интенсивно использующих пользовательского интерфейса, а также время, затраченное на приложение Создание инструкций SQL обычно небольшие по сравнению с временем, пользователь проводит ввод критериев.
