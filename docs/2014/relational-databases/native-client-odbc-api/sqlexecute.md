---
title: SQLExecute | Документы Microsoft
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
- SQLExecute function
ms.assetid: 4d7db8b6-611f-4fe4-be85-2a407059de45
caps.latest.revision: 14
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: c422b06c23e2d8f42c48b3b7e03525e285db2769
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36096412"
---
# <a name="sqlexecute"></a>SQLExecute
  Если атрибут инструкции SQL_SOPT_SS_PARAM_FOCUS не установлен в 0, SQLExecute вернет значение SQL_ERROR и формирует диагностическую запись с кодом SQLSTATE = HY024 и сообщением «недопустимое значение атрибута SQL_SOPT_SS_PARAM_FOCUS (должен быть равен нулю во время выполнения)». Дополнительные сведения о SQL_SOPT_SS_PARAM_FOCUS см. в разделе [SQLSetStmtAttr](sqlsetstmtattr.md).  
  
## <a name="remarks"></a>Примечания  
 Дополнительные сведения о возвращающих табличные значения параметров см. в разделе [табличное значение параметры &#40;ODBC&#41;](../native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md).  
  
## <a name="see-also"></a>См. также  
 [SQLExecute](http://go.microsoft.com/fwlink/?LinkId=80708)   
 [Подробные сведения о реализации API-интерфейсов ODBC](odbc-api-implementation-details.md)  
  
  