---
title: Работа с ошибками обновлений | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- updates [ADO], dealing with failed updates
ms.assetid: 299c37bd-19ff-4261-8571-b9665687e075
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 6ba4b4189691bf907b3ad67db91a8534268a8ec0
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47616432"
---
# <a name="dealing-with-failed-updates"></a>Работа с ошибками обновлений
Если обновление завершается с ошибками, как устранить ошибки зависит от характера и серьезность ошибки и логику приложения. Тем не менее если базы данных используется совместно с другими пользователями, обычно возникает ошибка что кто-то другой поле изменяется перед выполнением. Ошибки такого типа называется конфликт. ADO обнаруживает подобную ситуацию и сообщает об ошибке.  
  
## <a name="remarks"></a>Примечания  
 При возникновении ошибки обновления, они будут окажетесь запертым на процедуру обработки ошибок. Фильтровать набор записей с константой adFilterConflictingRecords так, чтобы только конфликтующие строки являются видимыми. В этом примере стратегии разрешение ошибок является просто Печать автора имена и фамилии (au_fname и Фамилия_автора).  
  
 Код, чтобы предупредить пользователя конфликт обновления выглядит следующим образом:  
  
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
