---
title: Работа с ошибками обновлений | Документы Microsoft
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- updates [ADO], dealing with failed updates
ms.assetid: 299c37bd-19ff-4261-8571-b9665687e075
caps.latest.revision: 3
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 3e5e2524d177d2f47ba4a0c9bc97dd76856bcb09
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="dealing-with-failed-updates"></a>Работа с ошибками обновлений
Если обновление завершается с ошибками, как устранить ошибки зависит от характер и серьезность ошибки и логике приложения. Тем не менее если базы данных используется совместно с другими пользователями, типичная ошибка происходит, кто изменяет поле, прежде чем выполнять. Ошибки такого типа называется конфликт. ADO обнаруживает подобную ситуацию и сообщает об ошибке.  
  
## <a name="remarks"></a>Замечания  
 В случае ошибки обновления, они будут выполняться в процедуру обработки ошибок. Фильтрация набора записей с константой adFilterConflictingRecords, чтобы были видны только конфликтующих строк. В этом примере стратегии разрешение ошибок является просто Печать автора имена и фамилии (Фамилия_автора и Фамилия_автора).  
  
 Код, чтобы предупредить пользователя о конфликт обновления выглядит следующим образом:  
  
```  
objRs.Filter = adFilterConflictingRecords  
objRs.MoveFirst  
Do While Not objRst.EOF  
   Debug.Print "Conflict: Name =  "; objRs!au_fname; " "; objRs!au_lname  
   objRs.MoveNext  
Loop  
```  
  
## <a name="see-also"></a>См. также  
 [Пакетный режим](../../../ado/guide/data/batch-mode.md)
