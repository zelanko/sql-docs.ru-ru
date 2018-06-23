---
title: Выполнение инструкций (ODBC) | Документы Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, statements
- statements [ODBC]
- ODBC applications, statements
- statements [ODBC], executing
ms.assetid: 063fc40d-ff81-490d-9c9b-2faefb729f37
caps.latest.revision: 32
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: ff5f9dcc3d8087418e3003dedc7f57e56840cba0
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36188996"
---
# <a name="executing-statements-odbc"></a>Выполнение инструкций (ODBC)
  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Драйвер ODBC собственного клиента предлагает различные способы выполнения инструкций SQL в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] базы данных:  
  
-   прямое выполнение;  
  
-   подготовленное выполнение.  
  
 Прямое выполнение включает в себя построение строки символов, содержащей [!INCLUDE[tsql](../../../includes/tsql-md.md)] оператор и его отправкой для выполнения с помощью **SQLExecDirect** функции. Подготовленное выполнение включает в себя построение строки символов, содержащей инструкцию [!INCLUDE[tsql](../../../includes/tsql-md.md)], и последующее выполнение этой инструкции в два шага. Первый этап использует [SQLPrepare, функция](http://go.microsoft.com/fwlink/?LinkId=59360) функцию для синтаксического анализа и компиляции плана выполнения для оператора в [!INCLUDE[ssDE](../../../includes/ssde-md.md)]. На втором шаге с помощью **SQLExecute** функцию для выполнения ранее подготовленный план выполнения. Это снижает расход ресурсов на синтаксический анализ и компиляцию при каждом выполнении. Подготовленное выполнение часто используется приложениями для многократного выполнения параметризованных инструкций SQL.  
  
 Как при непосредственном, так и при подготовленном выполнении может выполняться одиночная инструкция [!INCLUDE[tsql](../../../includes/tsql-md.md)] или пакет инструкций SQL, может также вызываться хранимая процедура.  
  
## <a name="in-this-section"></a>в этом разделе  
  
-   [Прямое выполнение](direct-execution.md)  
  
-   [Подготовленное выполнение](prepared-execution.md)  
  
-   [Процедуры](procedures.md)  
  
-   [Пакеты инструкций](batches-of-statements.md)  
  
-   [Действие параметров ISO](effects-of-iso-options.md)  
  
## <a name="see-also"></a>См. также  
 [Выполнение запросов &#40;ODBC&#41;](../executing-queries-odbc.md)  
  
  