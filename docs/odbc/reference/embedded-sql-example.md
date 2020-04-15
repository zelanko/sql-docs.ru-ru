---
title: Встроенный пример S'L Документы Майкрософт
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 39ec504c423817c6a3e11bc954555b201b8b09c6
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81294175"
---
# <a name="embedded-sql-example"></a>Пример Embedded SQL
Следующим кодом является простая встроенная программа S'L, написанная на C. Программа иллюстрирует многие, но не все, встроенных методов S'L. Программа подсказывает пользователю номер заказа, получает номер клиента, продавца и статус заказа, а также отображает полученную информацию на экране.  
  
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
  
 Обратите внимание на следующее о программе:  
  
-   **Переменные хозяина** Переменные хоста объявляются в **разделе,** приложенном keywords BEGIN DECLARE SECTION и **END DECLARE SECTION.** Каждое имя переменной хоста префиксировано толстой (:) когда он появляется во встроенном отчете S'L. Колотина позволяет прекомпилятору различать переменные хоста и объекты базы данных, такие как таблицы и столбцы, которые имеют одно и то же имя.  
  
-   **Типы данных** Типы данных, поддерживаемые DBMS и языком-хоста, могут быть совершенно разными. Это влияет на переменные хоста, поскольку они играют двойную роль. С одной стороны, переменные хоста являются программными переменными, декларируемыми и манипулируемыми операторами языка хоста. С другой стороны, они используются во встроенных заявлениях S'L для извлечения данных базы данных. Если нет типа языка-хозяина, который соответствовал бы типу данных DBMS, DBMS автоматически преобразует данные. Однако, поскольку каждый DBMS имеет свои собственные правила и особенности, связанные с процессом преобразования, типы переменных хоста должны быть выбраны тщательно.  
  
-   **Обработка ошибок** DBMS сообщает об ошибках в времени выполнения в программе приложений через зону связи S'L, или S'LCA. В предыдущем примере кода первым встроенным заявлением в области S-L является INCLUDE S'LCA. Это говорит о том, что прекомпилайзер должен включить в программу структуру S'LCA. Это необходимо всякий раз, когда программа будет обрабатывать ошибки, возвращенные DBMS. КОГДА... Выписка GOTO сообщает прекомпилятору для создания кода обработки ошибок, который ветвится к определенной метке при возникновении ошибки.  
  
-   **Синглтон СЕЛЕ** Заявление, используемое для возврата данных, является однотонным заявлением SELECT; то есть, он возвращает только один ряд данных. Таким образом, пример кода не декларирует и не использует курсоры.
