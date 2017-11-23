---
title: "Динамические курсоры | Документы Microsoft"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: guide
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- cursors [ADO], dynamic
- dynamic cursors [ADO]
ms.assetid: 00460f30-8cf7-494e-82df-41012f40ae51
caps.latest.revision: "6"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 72bbc7c35ef9f1b3f25336f4608ab70978f704ff
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="dynamic-cursors"></a>Динамические курсоры
Динамические курсоры обнаруживают все изменения, сделанные в строках в результирующем наборе, независимо от того, изменения выполняются ли из внутри курсора или другими пользователями за пределами курсора. Все инструкции insert, update и инструкций delete, выполняемые пользователями, видимы посредством курсора. Динамический курсор может обнаружить изменения, внесенные в строки, порядок и значения в результирующем наборе после открытия курсора. Обновления, сделанные вне курсора не видны до момента фиксации (если только уровень изоляции транзакций курсора имеет значение «uncommitted»).  
  
 Предположим, например, динамический курсор извлекает две строки и другим приложением и обновляет один из этих строк и удаляет другой. Если динамический курсор, затем выбирает строки, не позволяет найти удаленную строку, но он будет отображать новые значения для измененной строки.  
  
 Динамический курсор является хорошим выбором, если приложение должно определять все параллельные обновления, сделанные другими пользователями. Используйте **adOpenDynamic CursorTypeEnum** для указания, что вы хотите использовать динамический курсор в ADO.  
  
## <a name="see-also"></a>См. также:  
 [Однопроходные курсоры](../../../ado/guide/data/forward-only-cursors.md)   
 [Статические курсоры](../../../ado/guide/data/static-cursors.md)   
 [Курсоры ключевого набора](../../../ado/guide/data/keyset-cursors.md)
