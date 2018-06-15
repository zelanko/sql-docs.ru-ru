---
title: Процедуры | Документы Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: native-client-odbc-queries
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- stored procedures [ODBC]
- stored procedures [ODBC], about ODBC stored procedures
- ODBC applications, statements
- statements [ODBC], stored procedures
- ODBC applications, stored procedures
ms.assetid: c64d5f3a-376b-48ef-84f3-b6148ac8600a
caps.latest.revision: 30
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 3ae7aedfbbfc37a1ec4bfc1eb4b547b78e531df1
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
ms.locfileid: "32944649"
---
# <a name="procedures"></a>Процедуры
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../../includes/snac-deprecated.md)]

  Хранимая процедура представляет собой заранее скомпилированный исполняемый объект, содержащий одну или несколько инструкций [!INCLUDE[tsql](../../../includes/tsql-md.md)]. Хранимые процедуры могут иметь входные и выходные параметры, а также возвращать целочисленный код возврата. Приложение может перечислять существующие хранимые процедуры с помощью функций для работы с каталогами.  
  
 Приложения ODBC для [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] должны вызывать хранимые процедуры только методом прямого выполнения. При подключении к более ранним версиям [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] реализует драйвер ODBC для собственного клиента [SQLPrepare, функция](http://go.microsoft.com/fwlink/?LinkId=59360) путем создания временной хранимой процедуры, которая затем вызывается на **SQLExecute**. Он добавляет нагрузку по **SQLPrepare** создания временной хранимой процедуры, который только вызывает целевую хранимую процедуру или непосредственно исполнением целевой хранимой процедуры. Даже если соединение с базой данных [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] уже существует, подготовка вызова требует лишнего цикла приема-передачи данных по сети и построения плана выполнения, который только вызывает план выполнения хранимой процедуры.  
  
 При выполнении хранимой процедуры приложения ODBC должны использовать конструкцию ODBC CALL. Драйвер оптимизирован так, что при обработке конструкции ODBC CALL использует механизм удаленного вызова процедур (RPC). Это эффективнее, чем механизм, используемый для посылки инструкции [!INCLUDE[tsql](../../../includes/tsql-md.md)] EXECUTE на сервер.  
  
 Дополнительные сведения см. в разделе [выполнение хранимых процедур](../../../relational-databases/native-client-odbc-stored-procedures/running-stored-procedures.md).  
  
## <a name="see-also"></a>См. также:  
 [Выполнение инструкции & #40; ODBC & #41;](../../../relational-databases/native-client-odbc-queries/executing-statements/executing-statements-odbc.md)  
  
  
