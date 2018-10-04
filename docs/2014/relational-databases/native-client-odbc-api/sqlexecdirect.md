---
title: SQLExecDirect | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQLExecDirect function
ms.assetid: e7c2a5b5-83f4-4c72-9aca-7b9fb4748b11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 08fc098068080730b157d6bfb5aaf0b2b8842226
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48200555"
---
# <a name="sqlexecdirect"></a>SQLExecDirect
  Если атрибут инструкции SQL_SOPT_SS_PARAM_FOCUS не 0, SQLExecDirect вернет значение SQL_ERROR и формирует диагностическую запись с кодом SQLSTATE = HY024 и сообщением «недопустимое значение атрибута, SQL_SOPT_SS_PARAM_FOCUS (должен быть равен нулю во время выполнения)». Дополнительные сведения об атрибуте SQL_SOPT_SS_PARAM_FOCUS см. в разделе [SQLSetStmtAttr](sqlsetstmtattr.md).  
  
 Дополнительные сведения о возвращающих табличные значения параметров, см. в разделе [возвращающего табличное значение параметров &#40;ODBC&#41;](../native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md).  
  
## <a name="see-also"></a>См. также  
 [SQLExecDirect](http://go.microsoft.com/fwlink/?LinkId=80709)   
 [Подробные сведения о реализации API-интерфейсов ODBC](odbc-api-implementation-details.md)  
  
  
