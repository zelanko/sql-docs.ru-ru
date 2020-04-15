---
title: Подготовленное исполнение Документы Майкрософт
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
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 8265ed80028d5d8ac9696853a29474552f401f3e
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81297924"
---
# <a name="prepared-execution"></a>Подготовленное выполнение
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  API-интерфейс ODBC определяет подготовленное выполнение как способ уменьшить расходы на синтаксический анализ и компиляцию, связанные с повторным выполнением инструкции [!INCLUDE[tsql](../../../includes/tsql-md.md)]. Приложение строит строку символов, содержащую инструкцию SQL, а затем выполняет ее в два этапа. Он вызывает [функцию S'LPrepare](https://go.microsoft.com/fwlink/?LinkId=59360) один раз, чтобы разогнать и скомпилировать выписку в план [!INCLUDE[ssDE](../../../includes/ssde-md.md)]выполнения. Затем он вызывает **S'LExecute** для каждого выполнения подготовленного плана выполнения. Это снижает расход ресурсов на синтаксический анализ и компиляцию при каждом выполнении. Подготовленное выполнение часто используется приложениями для многократного выполнения параметризованных инструкций SQL.  
  
 В большинстве баз данных подготовленное выполнение инструкций, которые выполняются более трех или четырех раз, быстрее, чем прямое выполнение, в первую очередь потому, что инструкция компилируется только один раз, в то время как инструкции, выполняемые прямо, компилируются при каждом выполнении. Подготовленное выполнение может также снизить объем сетевого трафика, поскольку драйвер при каждом выполнении инструкции может передавать источнику данных идентификатор плана выполнения и значения параметров, а не целую инструкцию SQL.  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]уменьшает разницу в производительности между прямым и подготовленным выполнением с помощью усовершенствованных алгоритмов обнаружения и повторного использования планов выполнения от **S'LExecDirect.** В результате некоторые преимущества производительности выполнения подготовленных инструкций распространяются на прямое выполнение инструкций. Для получения дополнительной информации [см.](../../../relational-databases/native-client-odbc-queries/executing-statements/direct-execution.md)  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] также обеспечивает собственную поддержку подготовленного выполнения. План выполнения построен на **S'LPrepare,** а затем выполняется при вызове **S'LExecute.** Поскольку [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] не требуется создавать временные сохраненные процедуры на **S'LPrepare,** нет никаких дополнительных накладных расходов на системных таблицах в **tempdb.**  
  
 По причинам производительности подготовка оператора откладывается **до** тех пор, пока не будет вызвана операция метасобственности (например, [S'LDescribeCol](../../../relational-databases/native-client-odbc-api/sqldescribecol.md) или [S'LDescribeParam](../../../relational-databases/native-client-odbc-api/sqldescribeparam.md) в ODBC). Это поведение установлено по умолчанию. Любые ошибки в подготавливаемой инструкции неизвестны до выполнения инструкции или до выполнения операции над метасвойством. Установив атрибут инструкции SQL_SOPT_SS_DEFER_PREPARE в специфичное для ODBC-драйвера собственного клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] значение SQL_DP_OFF, можно отключить это поведение по умолчанию.  
  
 В случае отсроченной подготовки, вызов либо **S'LDescribeCol** или **S'LDescribeParam** перед вызовом **S'LExecute** генерирует дополнительную поездку туда и обратно на сервер. На **s'LDescribeCol**, водитель удаляет пункт WHERE из запроса и отправляет его на сервер с SET FMTONLY ON, чтобы получить описание столбцов в первом наборе результатов, возвращенных запросом. На **sLDescribeParam**, водитель вызывает сервер, чтобы получить описание выражений или столбцов, на которые ссылаются любые параметры маркеров в запросе. Этот метод также имеет несколько ограничений, таких как невозможность обработки параметров вложенных запросов.  
  
 Чрезмерное использование **S'LPrepare** с драйвером [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC ухудшает производительность, особенно при подключении к более ранним версиям сервера S'L. Не следует использовать подготовленное выполнение для инструкций, исполняемых один раз. Подготовленное выполнение медленнее, чем прямое выполнение, для однократного выполнения инструкции, потому что оно требует дополнительного обращения клиента к серверу. В предыдущих версиях [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] оно также создает временную хранимую процедуру.  
  
 В [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] подготовленные инструкции нельзя применять для создания временных объектов.  
  
 Некоторые ранние приложения ODBC использовали **S'LPrepare** в любое время [использования S'LBindParameter.](../../../relational-databases/native-client-odbc-api/sqlbindparameter.md) **СЗЛБиндпарамстер** не требует использования **S'LPrepare,** он может быть использован с **s'LExecDirect**. Например, для получения обратного кода или выходных параметров из сохраненной процедуры, которая выполняется только один раз, используйте **s'LExecDirect** с **помощью S'LBindParameter.** Не используйте **S'LPrepare** с **помощью S'LBindParameter,** если одно и то же заявление не будет выполнено несколько раз.  
  
## <a name="see-also"></a>См. также:  
 [Выполнение заявлений &#40;&#41;ODBC](../../../relational-databases/native-client-odbc-queries/executing-statements/executing-statements-odbc.md)  
  
  
