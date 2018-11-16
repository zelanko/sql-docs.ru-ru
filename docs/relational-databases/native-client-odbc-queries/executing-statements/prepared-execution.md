---
title: Подготовленное выполнение | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- deferred statement preparation
- prepared execution [ODBC]
- SQLPrepare function
- ODBC applications, statements
- SQLExecute function
- statements [ODBC], prepared execution
ms.assetid: f3a9d32b-6cd7-4f0c-b38d-c8ccc4ee40c3
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 777624a6dc7bf85ee618f586319aa6dc0c719e56
ms.sourcegitcommit: 9c6a37175296144464ffea815f371c024fce7032
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/15/2018
ms.locfileid: "51662463"
---
# <a name="prepared-execution"></a>Подготовленное выполнение
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../../includes/snac-deprecated.md)]

  API-интерфейс ODBC определяет подготовленное выполнение как способ уменьшить расходы на синтаксический анализ и компиляцию, связанные с повторным выполнением инструкции [!INCLUDE[tsql](../../../includes/tsql-md.md)]. Приложение строит строку символов, содержащую инструкцию SQL, а затем выполняет ее в два этапа. Он вызывает [функция SQLPrepare](https://go.microsoft.com/fwlink/?LinkId=59360) один раз, чтобы оператор анализируются и компилируются в план выполнения, [!INCLUDE[ssDE](../../../includes/ssde-md.md)]. Затем он вызывает **SQLExecute** для каждого выполнения подготовленного плана выполнения. Это снижает расход ресурсов на синтаксический анализ и компиляцию при каждом выполнении. Подготовленное выполнение часто используется приложениями для многократного выполнения параметризованных инструкций SQL.  
  
 В большинстве баз данных подготовленное выполнение инструкций, которые выполняются более трех или четырех раз, быстрее, чем прямое выполнение, в первую очередь потому, что инструкция компилируется только один раз, в то время как инструкции, выполняемые прямо, компилируются при каждом выполнении. Подготовленное выполнение может также снизить объем сетевого трафика, поскольку драйвер при каждом выполнении инструкции может передавать источнику данных идентификатор плана выполнения и значения параметров, а не целую инструкцию SQL.  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] различие в производительности между выполнением прямых и подготовленных за счет улучшения алгоритмов обнаружения и повторному использованию планов выполнения в **SQLExecDirect**. В результате некоторые преимущества производительности выполнения подготовленных инструкций распространяются на прямое выполнение инструкций. Дополнительные сведения см. в разделе [прямое выполнение](../../../relational-databases/native-client-odbc-queries/executing-statements/direct-execution.md).  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] также обеспечивает собственную поддержку подготовленного выполнения. План выполнения строится на **SQLPrepare** и при последующем выполнении **SQLExecute** вызывается. Так как [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] не обязана строить временные хранимые процедуры **SQLPrepare**, нет дополнительных издержек в системных таблицах в **tempdb**.  
  
 Из соображений производительности Подготовка инструкции откладывается до **SQLExecute** вызывается или операции над метасвойством (такой как [SQLDescribeCol](../../../relational-databases/native-client-odbc-api/sqldescribecol.md) или [SQLDescribeParam](../../../relational-databases/native-client-odbc-api/sqldescribeparam.md)в ODBC) выполняется. Это поведение по умолчанию. Любые ошибки в подготавливаемой инструкции неизвестны до выполнения инструкции или до выполнения операции над метасвойством. Установив атрибут инструкции SQL_SOPT_SS_DEFER_PREPARE в специфичное для ODBC-драйвера собственного клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] значение SQL_DP_OFF, можно отключить это поведение по умолчанию.  
  
 В случае отложенной подготовки, вызывая **SQLDescribeCol** или **SQLDescribeParam** перед вызовом **SQLExecute** создает дополнительное обращение к серверу. На **SQLDescribeCol**, драйвер удаляет предложение WHERE из запроса и отправляет его на сервер с помощью SET FMTONLY ON для получения описания столбцов в первом наборе результатов, возвращаемых запросом. На **SQLDescribeParam**, драйвер обращается к серверу для получения описания выражений или столбцов, ссылается любой маркер параметра в запросе. Этот метод также имеет несколько ограничений, таких как невозможность обработки параметров вложенных запросов.  
  
 Злоупотребление использованием **SQLPrepare** с [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] драйвер ODBC собственного клиента снижает производительность, особенно в том случае, при подключении к более ранним версиям SQL Server. Не следует использовать подготовленное выполнение для инструкций, исполняемых один раз. Подготовленное выполнение медленнее, чем прямое выполнение, для однократного выполнения инструкции, потому что оно требует дополнительного обращения клиента к серверу. В предыдущих версиях [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] оно также создает временную хранимую процедуру.  
  
 В [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] подготовленные инструкции нельзя применять для создания временных объектов.  
  
 Некоторые ранние ODBC-приложения используется **SQLPrepare** любое время [SQLBindParameter](../../../relational-databases/native-client-odbc-api/sqlbindparameter.md) было использовано. **SQLBindParameter** не требует применения **SQLPrepare**, он может использоваться с **SQLExecDirect**. Например, использовать **SQLExecDirect** с **SQLBindParameter** для получения кода возврата или выходных параметров хранимой процедуры, которая только один раз. Не используйте **SQLPrepare** с **SQLBindParameter** Если же инструкция будет выполняться несколько раз.  
  
## <a name="see-also"></a>См. также  
 [Выполнение инструкций &#40;ODBC&#41;](../../../relational-databases/native-client-odbc-queries/executing-statements/executing-statements-odbc.md)  
  
  
