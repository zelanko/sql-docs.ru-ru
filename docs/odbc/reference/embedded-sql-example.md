---
title: Пример внедренного SQL | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQL [ODBC], embedded SQL
- SQL statements [ODBC], embedded SQL
- embedded SQL [ODBC]
ms.assetid: b8a26e05-3c82-4c5f-8f01-9de0edb645e9
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 966962bdda79a57e83a0bce06b9254267efb474c
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68068662"
---
# <a name="embedded-sql-example"></a>Пример Embedded SQL
Следующий код представляет собой простую внедренную программу SQL, написанную на языке C. Программа иллюстрирует многие, но не все встроенные приемы SQL. Программа запрашивает у пользователя номер заказа, получает номер клиента, менеджера по продажам и состояние заказа, а также отображает полученные сведения на экране.  
  
```cpp  
int main() {  
   EXEC SQL INCLUDE SQLCA;  
   EXEC SQL BEGIN DECLARE SECTION;  
      int OrderID;         /* Employee ID (from user)         */  
      int CustID;            /* Retrieved customer ID         */  
      char SalesPerson[10]   /* Retrieved salesperson name      */  
      char Status[6]         /* Retrieved order status        */  
   EXEC SQL END DECLARE SECTION;  
  
   /* Set up error processing */  
   EXEC SQL WHENEVER SQLERROR GOTO query_error;  
   EXEC SQL WHENEVER NOT FOUND GOTO bad_number;  
  
   /* Prompt the user for order number */  
   printf ("Enter order number: ");  
   scanf_s("%d", &OrderID);  
  
   /* Execute the SQL query */  
   EXEC SQL SELECT CustID, SalesPerson, Status  
      FROM Orders  
      WHERE OrderID = :OrderID  
      INTO :CustID, :SalesPerson, :Status;  
  
   /* Display the results */  
   printf ("Customer number:  %d\n", CustID);  
   printf ("Salesperson: %s\n", SalesPerson);  
   printf ("Status: %s\n", Status);  
   exit();  
  
query_error:  
   printf ("SQL error: %ld\n", sqlca->sqlcode);  
   exit();  
  
bad_number:  
   printf ("Invalid order number.\n");  
   exit();  
}  
```  
  
 Обратите внимание на следующие сведения об этой программе:  
  
-   **Переменные узла** Переменные узла объявляются в разделе, заключенном в ключевые слова **Begin Declare Section** и **End Declare Section** . Каждое имя переменной узла имеет префикс с двоеточием (:) При появлении в внедренной инструкции SQL. Двоеточие позволяет предкомпилятору различать переменные узла и объекты базы данных, такие как таблицы и столбцы, имеющие одинаковое имя.  
  
-   **Типы данных** Типы данных, поддерживаемые СУБД и основным языком, могут быть весьма разными. Это влияет на переменные узла, так как они играют две роли. С одной стороны, переменные главного приложения — это переменные программы, которые объявляются и обрабатываются инструкциями языка узла. С другой стороны, они используются во внедренных инструкциях SQL для получения данных базы данных. Если тип языка узла, соответствующий типу данных СУБД, отсутствует, СУБД автоматически преобразует данные. Однако, поскольку каждая СУБД имеет свои собственные правила и особенности, связанные с процессом преобразования, типы переменных узла необходимо тщательно выбирать.  
  
-   **Обработка ошибок** СУБД сообщает об ошибках во время выполнения приложений через область взаимодействия SQL или СКЛКА. В предыдущем примере кода первая внедренная инструкция SQL включает в себя СКЛКА. Это указывает, что предкомпилятор должен включить в программу структуру СКЛКА. Это необходимо всякий раз, когда программа будет обрабатывать ошибки, возвращенные СУБД. В любом случае... Оператор GOTO сообщает предварительной компилятору о необходимости создания кода обработки ошибок, который выполняет переход к определенной метке при возникновении ошибки.  
  
-   **Единичное выделение** Инструкция, используемая для возврата данных, является одноэлементной инструкцией SELECT. то есть он возвращает только одну строку данных. Поэтому в примере кода не объявляются и не используются курсоры.
