---
title: Embedded SQL пример | Документация Майкрософт
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
manager: craigg
ms.openlocfilehash: eeab20c5385b02a874908cc941c1c69910efa228
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "65536663"
---
# <a name="embedded-sql-example"></a>Пример Embedded SQL
Ниже приведен простой embedded SQL программа, написанная на языке C. Программа показаны многие, но не все, внедренные методы SQL. Программа запрашивает у пользователя номер заказа, получает номер клиента, менеджеров по продажам и состояния заказа и выводит полученные сведения на экран.  
  
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
  
 Обратите внимание на следующие особенности этой программы.  
  
-   **Разместить переменные** узла переменные объявляются в разделе, заключенных **разделе ОБЪЯВИТЬ работы** и **ОБЪЯВИТЬ в КОНЦЕ РАЗДЕЛА** ключевые слова. Каждое имя переменной узла, отмеченную символом двоеточия (:) в внедренную инструкцию SQL. Двоеточие позволяет предварительной компиляции для различения хост-переменных и объектов базы данных, таких как таблицы и столбцы, с тем же именем.  
  
-   **Типы данных** типы данных, поддерживаемые СУБД и базовым языком может быть совершенно другим. Это влияет на хост-переменных, так как они играют двоякую роль. С одной стороны хост-переменных являются программные переменные, объявленные и манипулируется классом инструкции языка узла. С другой стороны они используются в инструкциях embedded SQL для получения данных базы данных. Если отсутствует тип узла язык, соответствующий типу данных СУБД, СУБД автоматически преобразует данные. Тем не менее так как каждый СУБД имеет свои собственные правила и особенности, связанные с процессом преобразования, типы переменных узла следует тщательно выбирать.  
  
-   **Обработка ошибок** СУБД сообщает об ошибках времени выполнения в программу приложения через области связи SQL, или SQLCA. В предыдущем примере первый внедренный оператор SQL — ВКЛЮЧАЮТ SQLCA. Сообщает о предварительной компиляции для включения в программу структуре SQLCA. Это необходимо, каждый раз, когда программа будет обрабатывать ошибки, возвращенные СУБД. WHENEVER... Инструкция GOTO указывает предварительной компиляции для создания кода обработки ошибок, выполняемое ветвей для определенной метки при возникновении ошибки.  
  
-   **Одноэлементный ВЫБЕРИТЕ** оператор, используемый для возврата данных является инструкцией SELECT singleton; то есть он возвращает только одну строку данных. Таким образом в примере кода не объявлять и использовать курсоры.
