---
title: SQLExecute | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQLExecute function
ms.assetid: 4d7db8b6-611f-4fe4-be85-2a407059de45
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: fab0ac676e4d0fc1b9d74c4aa9d1e472b8316a7e
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48095302"
---
# <a name="sqlexecute"></a>SQLExecute
  Если атрибут инструкции SQL_SOPT_SS_PARAM_FOCUS не имеет значение 0, SQLExecute вернет значение SQL_ERROR и формирует диагностическую запись с кодом SQLSTATE = HY024 и сообщением «недопустимое значение атрибута, SQL_SOPT_SS_PARAM_FOCUS (должен быть равен нулю во время выполнения)». Дополнительные сведения об атрибуте SQL_SOPT_SS_PARAM_FOCUS см. в разделе [SQLSetStmtAttr](sqlsetstmtattr.md).  
  
## <a name="remarks"></a>Примечания  
 Дополнительные сведения о возвращающих табличные значения параметров, см. в разделе [возвращающего табличное значение параметров &#40;ODBC&#41;](../native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md).  
  
## <a name="see-also"></a>См. также  
 [SQLExecute](http://go.microsoft.com/fwlink/?LinkId=80708)   
 [Подробные сведения о реализации API-интерфейсов ODBC](odbc-api-implementation-details.md)  
  
  
