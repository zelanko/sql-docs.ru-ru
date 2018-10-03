---
title: Выполнение инструкций (ODBC) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, statements
- statements [ODBC]
- ODBC applications, statements
- statements [ODBC], executing
ms.assetid: 063fc40d-ff81-490d-9c9b-2faefb729f37
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 552ef613caadd2aa421a709ad7f351ac4f529e12
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47803842"
---
# <a name="executing-statements-odbc"></a>Выполнение инструкций (ODBC)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../../includes/snac-deprecated.md)]

  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Драйвер ODBC собственного клиента предлагает различные способы выполнения инструкций SQL в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] базы данных:  
  
-   прямое выполнение;  
  
-   подготовленное выполнение.  
  
 Прямое выполнение включает в себя построение строки символов, содержащей [!INCLUDE[tsql](../../../includes/tsql-md.md)] инструкции и его отправки для выполнения с помощью **SQLExecDirect** функции. Подготовленное выполнение включает в себя построение строки символов, содержащей инструкцию [!INCLUDE[tsql](../../../includes/tsql-md.md)], и последующее выполнение этой инструкции в два шага. На первом шаге с помощью [функция SQLPrepare](http://go.microsoft.com/fwlink/?LinkId=59360) функция синтаксический анализ и создается план выполнения инструкции в [!INCLUDE[ssDE](../../../includes/ssde-md.md)]. На втором шаге с помощью **SQLExecute** функция, выполняемая ранее подготовленный план выполнения. Это снижает расход ресурсов на синтаксический анализ и компиляцию при каждом выполнении. Подготовленное выполнение часто используется приложениями для многократного выполнения параметризованных инструкций SQL.  
  
 Как при непосредственном, так и при подготовленном выполнении может выполняться одиночная инструкция [!INCLUDE[tsql](../../../includes/tsql-md.md)] или пакет инструкций SQL, может также вызываться хранимая процедура.  
  
## <a name="in-this-section"></a>в этом разделе  
  
-   [Прямое выполнение](../../../relational-databases/native-client-odbc-queries/executing-statements/direct-execution.md)  
  
-   [Подготовленное выполнение](../../../relational-databases/native-client-odbc-queries/executing-statements/prepared-execution.md)  
  
-   [Процедуры](../../../relational-databases/native-client-odbc-queries/executing-statements/procedures.md)  
  
-   [Пакеты инструкций](../../../relational-databases/native-client-odbc-queries/executing-statements/batches-of-statements.md)  
  
-   [Действие параметров ISO](../../../relational-databases/native-client-odbc-queries/executing-statements/effects-of-iso-options.md)  
  
## <a name="see-also"></a>См. также  
 [Выполнение запросов &#40;ODBC&#41;](../../../relational-databases/native-client-odbc-queries/executing-queries-odbc.md)  
  
  
