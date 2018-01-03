---
title: "Внедренные пример SQL | Документы Microsoft"
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
- SQL [ODBC], embedded SQL
- SQL statements [ODBC], embedded SQL
- embedded SQL [ODBC]
ms.assetid: b8a26e05-3c82-4c5f-8f01-9de0edb645e9
caps.latest.revision: "7"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 13890248b3e724f2a41db5a3425c62dc7635b63a
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="embedded-sql-example"></a>Пример Embedded SQL
В следующем коде показан простой встроенной программы SQL, написана на языке C. Программа иллюстрирует многие, но не всех встроенный приемы SQL. Программа запросит у пользователя номер заказа, получает номер клиента, менеджер по продажам и состояние заказа и выводит полученные сведения на экран.  
  
```  
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
  
-   **Разместить переменные** узла переменные объявляются в разделе, заключенных в **НАЧАТЬ ОБЪЯВИТЕ РАЗДЕЛ** и **ОБЪЯВЛЕНИЯ в КОНЦЕ РАЗДЕЛА** ключевые слова. Имя каждой переменной узла предваряется двоеточие (:), когда он появится в embedded SQL-инструкции. Двоеточие позволяет предварительной компиляции для различения хост-переменных и объектов базы данных, таких как таблицы и столбцы, которые имеют одинаковое имя.  
  
-   **Типы данных** может быть довольно разные типы данных, поддерживаемые СУБД и базовым языком. Это влияет на хост-переменных, так как они играют роль два. С одной стороны хост-переменных являются программные переменные, объявленные и управляемое системой узла инструкций языка. С другой стороны они используются в инструкциях embedded SQL для получения данных базы данных. Если нет типов языка узла, соответствующий типу данных СУБД, СУБД автоматически преобразует данные. Тем не менее поскольку каждый СУБД имеет свои собственные правила и особенности, связанные с процессом преобразования, типы переменных узла должно выбираться внимательно.  
  
-   **Обработка ошибок** СУБД сообщает программе приложений с помощью области связи SQL, или SQLCA ошибки во время выполнения. В предыдущем примере кода первый внедренный инструкция SQL является ВКЛЮЧАЮТ SQLCA. Это заставляет предварительной компиляции для включения структуры SQLCA в программе. Это необходимо, каждый раз, когда программа будет обрабатывать ошибки, возвращенные СУБД. WHENEVER... Оператор GOTO сообщает предварительной компиляции для создания кода обработки ошибок, происходящих ветви для определенной метки при возникновении ошибки.  
  
-   **Одноэлементный ВЫБЕРИТЕ** оператор, используемый для получения данных является инструкцией SELECT одноэлементный; то есть он возвращает только одну строку данных. Таким образом в примере кода не объявлять и использовать курсоры.
