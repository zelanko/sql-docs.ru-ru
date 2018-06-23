---
title: Выполнение хранимых процедур | Документы Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- ODBC, stored procedures
- stored procedures [ODBC], running
- SQL Server Native Client ODBC driver, stored procedures
- stored procedures [ODBC], executing
ms.assetid: 866b6dd3-2acd-4dfb-aeca-a0352b2d4c6a
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 54132acdb66095e45b5bdaf23b5f4b1c2716b538
ms.sourcegitcommit: a78fa85609a82e905de9db8b75d2e83257831ad9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/18/2018
ms.locfileid: "35699345"
---
# <a name="running-stored-procedures"></a>Выполнение хранимых процедур
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

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
  
     Пример вызова хранимой процедуры см. в разделе [процесса коды возврата и выходные параметры &#40;ODBC&#41;](../../relational-databases/native-client-odbc-how-to/running-stored-procedures-process-return-codes-and-output-parameters.md).  
  
## <a name="in-this-section"></a>в этом разделе  
  
-   [Вызов хранимой процедуры](../../relational-databases/native-client-odbc-stored-procedures/calling-a-stored-procedure.md)  
  
-   [Пакетная обработка вызовов хранимых процедур](../../relational-databases/native-client-odbc-stored-procedures/batching-stored-procedure-calls.md)  
  
-   [Обработка результатов хранимой процедуры](../../relational-databases/native-client-odbc-stored-procedures/processing-stored-procedure-results.md)  
  
## <a name="see-also"></a>См. также  
 [Собственный клиент SQL Server &#40;ODBC&#41;](../../relational-databases/native-client/odbc/sql-server-native-client-odbc.md)   
 [Выполнение хранимых процедур инструкции &#40;ODBC&#41;](http://msdn.microsoft.com/library/c2220182-a23d-4475-b353-77a77ab613d6)  
  
  
