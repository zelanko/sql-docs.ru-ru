---
title: "Как: Указание направления параметров с помощью драйвера SQLSRV | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: php
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: stored procedure support
ms.assetid: 1209eeca-df75-4283-96dc-714f39956b95
caps.latest.revision: "16"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 692d1cd432a7d156a4bb9d8cc2c3bfcf57c02d6d
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/18/2017
---
# <a name="how-to-specify-parameter-direction-using-the-sqlsrv-driver"></a>Практическое руководство. Указание направления параметров с помощью драйвера SQLSRV
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Эта статья описывает использование драйвера SQLSRV для указания направления параметров при вызове хранимой процедуры. Обратите внимание, что направление параметров указывается при создании параметра массива (шаг 3), который передается [sqlsrv_query](../../connect/php/sqlsrv-query.md) или [sqlsrv_prepare](../../connect/php/sqlsrv-prepare.md).  
  
### <a name="to-specify-parameter-direction"></a>Порядок указания направления параметров  
  
1.  Определите запрос Transact-SQL, который вызывает хранимую процедуру. Используйте вопросительные знаки (?) вместо параметров, передаваемых в хранимую процедуру. Например, эта строка вызывает хранимую процедуру (UpdateVacationHours), которая принимает два параметра:  
  
    ```  
    $tsql = "{call UpdateVacationHours(?, ?)}";  
    ```  
  
    > [!NOTE]  
    > Рекомендуется вызывать хранимые процедуры с использованием канонического синтаксиса. Дополнительные сведения о каноническом синтаксисе см. в статье [Вызов хранимой процедуры](http://go.microsoft.com/fwlink/?linkid=119517).  
  
2.  Инициализируйте или обновите переменные PHP, которые соответствуют заполнителям в запросе Transact-SQL. Например, следующий код инициализирует два параметра для хранимой процедуры UpdateVacationHours:  
  
    ```  
    $employeeId = 101;  
    $usedVacationHours = 8;  
    ```  
  
    > [!NOTE]  
    > Переменные, которые инициализируются или обновляются с использованием **null**, **DateTime**или типов потоков, нельзя использовать в качестве параметров вывода.  
  
3.  Используйте переменные PHP из шага 2, чтобы создать или обновить массив значений параметров, порядок которых соответствует заполнителям параметров в строке Transact-SQL. Укажите направление для каждого параметра в массиве. Направление каждого параметра определяется одним из двух способов: по умолчанию (для входных параметров) или с помощью **SQLSRV_PARAM_\***  константы (для вывода и двунаправленных параметров). Например, следующий код задает параметр *$employeeId* в качестве параметра ввода и параметр *$usedVacationHours* в качестве двунаправленного параметра:  
  
    ```  
    $params = array(  
                     array($employeeId, SQLSRV_PARAM_IN),  
                     array($usedVacationHours, SQLSRV_PARAM_INOUT)  
                    );  
    ```  
  
    Чтобы лучше понять синтаксис для указания направления параметра, предположим, что *$var1*, *$var2*и *$var3* соответствуют параметру ввода, параметру вывода и двунаправленному параметру. Направление параметров можно указать любым из следующих способов:  
  
    -   Укажите параметр ввода неявным образом, параметр вывода явным образом и двунаправленный параметр явным образом:  
  
        ```  
        array(   
               array($var1),  
               array($var2, SQLSRV_PARAM_OUT),  
               array($var3, SQLSRV_PARAM_INOUT)  
               );  
        ```  
  
    -   Укажите параметр ввода явным образом, параметр вывода явным образом и двунаправленный параметр явным образом:  
  
        ```  
        array(   
               array($var1, SQLSRV_PARAM_IN),  
               array($var2, SQLSRV_PARAM_OUT),  
               array($var3, SQLSRV_PARAM_INOUT)  
               );  
        ```  
  
4.  Выполнение запроса с [sqlsrv_query](../../connect/php/sqlsrv-query.md) или [sqlsrv_prepare](../../connect/php/sqlsrv-prepare.md) и [sqlsrv_execute](../../connect/php/sqlsrv-execute.md). Например, следующий код использует соединение *$conn* для выполнения запроса *$tsql* со значениями параметров, указанными в *$params*:  
  
    ```  
    sqlsrv_query($conn, $tsql, $params);  
    ```  
  
## <a name="see-also"></a>См. также:  
[Практическое руководство. Извлечение параметров вывода с помощью драйвера SQLSRV](../../connect/php/how-to-retrieve-output-parameters-using-the-sqlsrv-driver.md)  
[How to: Retrieve Input and Output Parameters Using the SQLSRV Driver](../../connect/php/how-to-retrieve-input-and-output-parameters-using-the-sqlsrv-driver.md)  
  
