---
title: Выполнение инструкций (ODBC) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
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
ms.openlocfilehash: 1517e17a7b0ecaf9137e3af21e076dacc2fd98f3
ms.sourcegitcommit: 334cae1925fa5ac6c140e0b2c38c844c477e3ffb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/13/2018
ms.locfileid: "53376996"
---
# <a name="executing-statements-odbc"></a>Выполнение инструкций (ODBC)
  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Драйвер ODBC собственного клиента предлагает различные способы выполнения инструкций SQL в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] базы данных:  
  
-   прямое выполнение;  
  
-   подготовленное выполнение.  
  
 Прямое выполнение включает в себя построение строки символов, содержащей [!INCLUDE[tsql](../../../includes/tsql-md.md)] инструкции и его отправки для выполнения с помощью **SQLExecDirect** функции. Подготовленное выполнение включает в себя построение строки символов, содержащей инструкцию [!INCLUDE[tsql](../../../includes/tsql-md.md)], и последующее выполнение этой инструкции в два шага. На первом шаге с помощью [функция SQLPrepare](https://go.microsoft.com/fwlink/?LinkId=59360) функция синтаксический анализ и создается план выполнения инструкции в [!INCLUDE[ssDE](../../../includes/ssde-md.md)]. На втором шаге с помощью **SQLExecute** функция, выполняемая ранее подготовленный план выполнения. Это снижает расход ресурсов на синтаксический анализ и компиляцию при каждом выполнении. Подготовленное выполнение часто используется приложениями для многократного выполнения параметризованных инструкций SQL.  
  
 Как при непосредственном, так и при подготовленном выполнении может выполняться одиночная инструкция [!INCLUDE[tsql](../../../includes/tsql-md.md)] или пакет инструкций SQL, может также вызываться хранимая процедура.  
  
## <a name="in-this-section"></a>в этом разделе  
  
-   [Прямое выполнение](direct-execution.md)  
  
-   [Подготовленное выполнение](prepared-execution.md)  
  
-   [Процедуры](procedures.md)  
  
-   [Пакеты инструкций](batches-of-statements.md)  
  
-   [Действие параметров ISO](effects-of-iso-options.md)  
  
## <a name="see-also"></a>См. также  
 [Выполнение запросов &#40;ODBC&#41;](../executing-queries-odbc.md)  
  
  
