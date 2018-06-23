---
title: Процедуры | Документы Microsoft
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
- stored procedures [ODBC]
- stored procedures [ODBC], about ODBC stored procedures
- ODBC applications, statements
- statements [ODBC], stored procedures
- ODBC applications, stored procedures
ms.assetid: c64d5f3a-376b-48ef-84f3-b6148ac8600a
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: a4e9576ce93b196968b28b6cc91cadd662d2a3fb
ms.sourcegitcommit: a78fa85609a82e905de9db8b75d2e83257831ad9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/18/2018
ms.locfileid: "35694895"
---
# <a name="procedures"></a>Процедуры
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../../includes/snac-deprecated.md)]

  Хранимая процедура представляет собой заранее скомпилированный исполняемый объект, содержащий одну или несколько инструкций [!INCLUDE[tsql](../../../includes/tsql-md.md)]. Хранимые процедуры могут иметь входные и выходные параметры, а также возвращать целочисленный код возврата. Приложение может перечислять существующие хранимые процедуры с помощью функций для работы с каталогами.  
  
 Приложения ODBC для [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] должны вызывать хранимые процедуры только методом прямого выполнения. При подключении к более ранним версиям [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] реализует драйвер ODBC для собственного клиента [SQLPrepare, функция](http://go.microsoft.com/fwlink/?LinkId=59360) путем создания временной хранимой процедуры, которая затем вызывается на **SQLExecute** . Он добавляет нагрузку по **SQLPrepare** создания временной хранимой процедуры, который только вызывает целевую хранимую процедуру или непосредственно исполнением целевой хранимой процедуры. Даже если соединение с базой данных [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] уже существует, подготовка вызова требует лишнего цикла приема-передачи данных по сети и построения плана выполнения, который только вызывает план выполнения хранимой процедуры.  
  
 При выполнении хранимой процедуры приложения ODBC должны использовать конструкцию ODBC CALL. Драйвер оптимизирован так, что при обработке конструкции ODBC CALL использует механизм удаленного вызова процедур (RPC). Это эффективнее, чем механизм, используемый для посылки инструкции [!INCLUDE[tsql](../../../includes/tsql-md.md)] EXECUTE на сервер.  
  
 Дополнительные сведения см. в разделе [выполнение хранимых процедур](../../../relational-databases/native-client-odbc-stored-procedures/running-stored-procedures.md).  
  
## <a name="see-also"></a>См. также  
 [Выполнение инструкций &#40;ODBC&#41;](../../../relational-databases/native-client-odbc-queries/executing-statements/executing-statements-odbc.md)  
  
  
