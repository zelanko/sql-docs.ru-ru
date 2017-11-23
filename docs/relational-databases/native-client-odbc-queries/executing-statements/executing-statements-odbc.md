---
title: "Выполнение инструкций (ODBC) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-odbc-queries
ms.reviewer: 
ms.suite: sql
ms.technology: docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, statements
- statements [ODBC]
- ODBC applications, statements
- statements [ODBC], executing
ms.assetid: 063fc40d-ff81-490d-9c9b-2faefb729f37
caps.latest.revision: "33"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: e617e4550766b7952961c3dae6830eaebdd2686a
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="executing-statements-odbc"></a>Выполнение инструкций (ODBC)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../../includes/snac-deprecated.md)]

  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Драйвер ODBC собственного клиента предлагает различные способы выполнения инструкций SQL в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] базы данных:  
  
-   прямое выполнение;  
  
-   подготовленное выполнение.  
  
 Прямое выполнение включает в себя построение строки символов, содержащей [!INCLUDE[tsql](../../../includes/tsql-md.md)] оператор и его отправкой для выполнения с помощью **SQLExecDirect** функции. Подготовленное выполнение включает в себя построение строки символов, содержащей инструкцию [!INCLUDE[tsql](../../../includes/tsql-md.md)], и последующее выполнение этой инструкции в два шага. Первый этап использует [SQLPrepare, функция](http://go.microsoft.com/fwlink/?LinkId=59360) функцию для синтаксического анализа и компиляции плана выполнения для оператора в [!INCLUDE[ssDE](../../../includes/ssde-md.md)]. На втором шаге с помощью **SQLExecute** функцию для выполнения ранее подготовленный план выполнения. Это снижает расход ресурсов на синтаксический анализ и компиляцию при каждом выполнении. Подготовленное выполнение часто используется приложениями для многократного выполнения параметризованных инструкций SQL.  
  
 Как при непосредственном, так и при подготовленном выполнении может выполняться одиночная инструкция [!INCLUDE[tsql](../../../includes/tsql-md.md)] или пакет инструкций SQL, может также вызываться хранимая процедура.  
  
## <a name="in-this-section"></a>В этом разделе  
  
-   [Прямое выполнение](../../../relational-databases/native-client-odbc-queries/executing-statements/direct-execution.md)  
  
-   [Подготовленное выполнение](../../../relational-databases/native-client-odbc-queries/executing-statements/prepared-execution.md)  
  
-   [Процедуры](../../../relational-databases/native-client-odbc-queries/executing-statements/procedures.md)  
  
-   [Пакеты инструкций](../../../relational-databases/native-client-odbc-queries/executing-statements/batches-of-statements.md)  
  
-   [Действие параметров ISO](../../../relational-databases/native-client-odbc-queries/executing-statements/effects-of-iso-options.md)  
  
## <a name="see-also"></a>См. также:  
 [Выполнение запросов &#40; ODBC &#41;](../../../relational-databases/native-client-odbc-queries/executing-queries-odbc.md)  
  
  
