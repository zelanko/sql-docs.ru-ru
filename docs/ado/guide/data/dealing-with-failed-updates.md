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
ms.openlocfilehash: d442a9c397ad184658f9101343e139697c9b3756
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67925639"
---
# <a name="dealing-with-failed-updates"></a>Работа с ошибками обновлений
Если обновление завершается с ошибками, как устранить ошибки зависит от характера и серьезность ошибки и логику приложения. Тем не менее если базы данных используется совместно с другими пользователями, обычно возникает ошибка что кто-то другой поле изменяется перед выполнением. Ошибки такого типа называется конфликт. ADO обнаруживает подобную ситуацию и сообщает об ошибке.  
  
## <a name="remarks"></a>Примечания  
 При возникновении ошибки обновления, они будут окажетесь запертым на процедуру обработки ошибок. Фильтровать набор записей с константой adFilterConflictingRecords так, чтобы только конфликтующие строки являются видимыми. В этом примере стратегии разрешение ошибок является просто Печать автора имена и фамилии (au_fname и Фамилия_автора).  
  
 Код, чтобы предупредить пользователя конфликт обновления выглядит следующим образом:  
  
```  
objRs.Filter = adFilterConflictingRecords  
objRs.MoveFirst  
Do While Not objRst.EOF  
   Debug.Print "Conflict: Name =  "; objRs!au_fname; " "; objRs!au_lname  
   objRs.MoveNext  
Loop  
```  
  
## <a name="see-also"></a>См. также  
 [Пакетный режим](../../../ado/guide/data/batch-mode.md)
