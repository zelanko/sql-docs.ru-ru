---
title: Работа с неудачными обновлениями | Документация Майкрософт
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
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "67925639"
---
# <a name="dealing-with-failed-updates"></a>Работа с ошибками обновлений
Когда обновление завершается с ошибками, способ устранения ошибок зависит от природы и серьезности ошибок и логики приложения. Однако если база данных используется совместно с другими пользователями, то типичная ошибка заключается в том, что другой пользователь изменяет поле до того, как это сделано. Этот тип ошибки называется конфликтом. ADO обнаруживает эту ситуацию и сообщает об ошибке.  
  
## <a name="remarks"></a>Remarks  
 При наличии ошибок обновления они будут перехвачены в подпрограммы обработки ошибок. Отфильтруйте набор записей с помощью константы Адфилтерконфликтингрекордс, чтобы отображались только конфликтующие строки. В этом примере стратегия разрешения ошибок — это просто печать первого и последнего имени автора (au_fname и au_lname).  
  
 Код для оповещения пользователя о конфликте обновлений выглядит следующим образом:  
  
```  
objRs.Filter = adFilterConflictingRecords  
objRs.MoveFirst  
Do While Not objRst.EOF  
   Debug.Print "Conflict: Name =  "; objRs!au_fname; " "; objRs!au_lname  
   objRs.MoveNext  
Loop  
```  
  
## <a name="see-also"></a>См. также:  
 [Пакетный режим](../../../ado/guide/data/batch-mode.md)
