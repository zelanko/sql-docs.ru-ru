---
title: "Статические курсоры | Документы Microsoft"
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
- cursors [ADO], static
- static cursors [ADO]
ms.assetid: cce93ace-c4ed-4c6c-940c-28a50ff2fd12
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 4442e8fe5464f1eb8c7e79fe4df347ae10959b36
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="static-cursors"></a>Статические курсоры
Статический курсор всегда отображает результирующий набор, в котором он был при первом открытии курсора. В зависимости от реализации, статические курсоры имеют только для чтения или чтения и записи и предоставить прямой и обратной прокрутки. Статический курсор обычно не обнаруживает изменений в членство, порядок и значения из результирующего набора, после открытия курсора. Статические курсоры могут обнаруживать свои собственные обновления, удаления и вставки, несмотря на то, что они не требуются для этого.  
  
 Статические курсоры никогда не обнаружить другие обновляет, удаляет и вставляет. Например предположим, статический курсор извлекает строки и другое приложение, а затем обновляет этой строки. Если приложение refetches строку из статического курсора, значения, которые видит не изменяются, независимо от изменений, внесенных в других приложениях. Поддерживаются все типы прокрутки, но поставщики могут или не поддерживает закладки.  
  
 Если приложения не требуется для обнаружения изменения данных и требуется прокрутка, статический курсор является лучшим вариантом. Используйте **adOpenStatic CursorTypeEnum** для указания, что вы хотите использовать статический курсор в ADO.  
  
## <a name="see-also"></a>См. также:  
 [Однопроходные курсоры](../../../ado/guide/data/forward-only-cursors.md)   
 [Управляемые набором ключей курсоры](../../../ado/guide/data/keyset-cursors.md)   
 [Динамические курсоры](../../../ado/guide/data/dynamic-cursors.md)
