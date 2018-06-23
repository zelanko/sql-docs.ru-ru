---
title: SQLExecDirect | Документы Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- SQLExecDirect function
ms.assetid: e7c2a5b5-83f4-4c72-9aca-7b9fb4748b11
caps.latest.revision: 13
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 7c51b1330f862dab23e028892945dce32f42d0e7
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36194710"
---
# <a name="sqlexecdirect"></a>SQLExecDirect
  Если атрибут инструкции SQL_SOPT_SS_PARAM_FOCUS не равно 0, SQLExecDirect вернет значение SQL_ERROR и формирует диагностическую запись с кодом SQLSTATE = HY024 и сообщением «недопустимое значение атрибута SQL_SOPT_SS_PARAM_FOCUS (должен быть равен нулю во время выполнения)». Дополнительные сведения о SQL_SOPT_SS_PARAM_FOCUS см. в разделе [SQLSetStmtAttr](sqlsetstmtattr.md).  
  
 Дополнительные сведения о возвращающих табличные значения параметров см. в разделе [табличное значение параметры &#40;ODBC&#41;](../native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md).  
  
## <a name="see-also"></a>См. также  
 [SQLExecDirect](http://go.microsoft.com/fwlink/?LinkId=80709)   
 [Подробные сведения о реализации API-интерфейсов ODBC](odbc-api-implementation-details.md)  
  
  