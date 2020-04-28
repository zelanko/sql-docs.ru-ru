---
title: Выполнение хранимых процедур | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- ODBC, stored procedures
- stored procedures [ODBC], running
- SQL Server Native Client ODBC driver, stored procedures
- stored procedures [ODBC], executing
ms.assetid: 866b6dd3-2acd-4dfb-aeca-a0352b2d4c6a
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 0b69a9177f98c8ee1096c18f368af12b11d6b325
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "81304556"
---
# <a name="running-stored-procedures"></a>Выполнение хранимых процедур
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Хранимая процедура представляет собой исполняемый объект, хранящийся в базе данных. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поддерживает:  
  
-   Хранимые процедуры  
  
     Одна или несколько инструкций SQL предварительно откомпилированы в одну исполняемую процедуру.  
  
-   Расширенные хранимые процедуры  
  
     Библиотеки динамических ссылок (DLL) C или C++, написанные с использованием API-интерфейса служб SQL Server Open Data Services для расширенных хранимых процедур. API-интерфейс служб Open Data Services расширяет возможности хранимых процедур, позволяя им использовать код на C или C++.  
  
 При выполнении инструкций путем вызова хранимой процедуры для источника данных (в противоположность непосредственному выполнению или подготовке инструкций в клиентском приложении) можно получить следующие преимущества.  
  
-   Более высокая производительность  
  
     Инструкции SQL анализируются и компилируются во время формирования процедур. Затем эта дополнительная нагрузка компенсируется при выполнении процедур.  
  
-   Снижение сетевых издержек  
  
     Когда вместо отправки по сети сложных запросов выполняется процедура, это способствует сокращению объема сетевого трафика. Если при выполнении хранимой процедуры приложение ODBC использует синтаксическую конструкцию ODBC {CALL}, драйвер ODBC принимает дополнительные меры по оптимизации, которые снимают необходимость преобразования данных параметров.  
  
-   Повышение уровня согласованности  
  
     Если правила организации реализованы в центральном ресурсе, таком, как хранимая процедура, их можно кодировать, тестировать и отлаживать в один прием. Затем индивидуальные программисты могут использовать эти протестированные хранимые процедуры, не разрабатывая собственных реализаций.  
  
-   Более высокая точность  
  
     Поскольку хранимые процедуры, как правило, создаются опытными программистами, они обычно бывают более эффективными и содержат меньше ошибок, нежели код, создаваемый многократно программистами различных уровней компетентности.  
  
-   Дополнительные функциональные возможности  
  
     В расширенных хранимых процедурах можно использовать средства на языках C и C++, недоступные в инструкциях [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
     Пример вызова хранимой процедуры см. в разделе [обработка кодов возврата и выходных параметров &#40;&#41;ODBC ](../../relational-databases/native-client-odbc-how-to/running-stored-procedures-process-return-codes-and-output-parameters.md).  
  
## <a name="in-this-section"></a>В этом разделе  
  
-   [Вызов хранимой процедуры](../../relational-databases/native-client-odbc-stored-procedures/calling-a-stored-procedure.md)  
  
-   [Создание пакетной обработки вызовов хранимых процедур](../../relational-databases/native-client-odbc-stored-procedures/batching-stored-procedure-calls.md)  
  
-   [Обработка результатов хранимой процедуры](../../relational-databases/native-client-odbc-stored-procedures/processing-stored-procedure-results.md)  
  
## <a name="see-also"></a>См. также:  
 [SQL Server Native Client &#40;ODBC&#41;](../../relational-databases/native-client/odbc/sql-server-native-client-odbc.md)   
 [Разделы руководства по выполнению хранимых процедур &#40;ODBC&#41;](https://msdn.microsoft.com/library/c2220182-a23d-4475-b353-77a77ab613d6)  
  
  
