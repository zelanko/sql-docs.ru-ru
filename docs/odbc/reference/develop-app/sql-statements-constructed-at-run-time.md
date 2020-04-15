---
title: Заявления, построенные в время выполнения (ru) Документы Майкрософт
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 795335be2a2a3aab1be6dac26bf6d213161fe42e
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81301975"
---
# <a name="sql-statements-constructed-at-run-time"></a>Инструкции SQL, сформированные во время выполнения
Приложения, выполняющие специальный анализ, обычно создают инструкции s-L во время выполнения. Например, электронная таблица может позволить пользователю выбрать столбцы, из которых можно получить данные:  
  
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
  
 Другим классом приложений, обычно конструированных операторами S'L во время выполнения, являются среды разработки приложений. Тем не менее, операторы, которые они строят, жестко закодированы в приложении, которое они строят, где они обычно могут быть оптимизированы и протестированы.  
  
 Приложения, которые строят операторы S'L во время выполнения, могут обеспечить огромную гибкость для пользователя. Как видно из предыдущего примера, который даже не поддерживал такие общие операции, как **положения WHERE,** оговорки **ORDER BY** или соединения, построение инструкций S'L во время выполнения значительно сложнее, чем заявления с жестким кодированием. Кроме того, тестирование таких приложений является проблематичным, поскольку они могут создавать произвольное количество инструкций по S'L.  
  
 Потенциальным недостатком построения инструкций s'L во время выполнения является то, что для построения оператора требуется гораздо больше времени, чем использование оператора с жестким кодом. К счастью, это редко вызывает озабоченность. Такие приложения, как правило, являются интенсивными для пользователей, и время, затрагиваемые приложением на построение инструкций по S'L, как правило, невелико по сравнению со временем, которое пользователь тратит на ввод критериев.
