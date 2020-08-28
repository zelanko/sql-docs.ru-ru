---
description: Свойство SortOrder (ADOX)
title: Свойство SortOrder (ADOX) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Column::SortOrder
- _Column::PutSortOrder
- _Column::put_SortOrder
- _Column::get_SortOrder
- _Column::GetSortOrder
helpviewer_keywords:
- SortOrder property [ADOX]
ms.assetid: 04510b19-9cb2-4895-b23b-f7790123eb04
author: rothja
ms.author: jroth
ms.openlocfilehash: 4141e657fd0c7dfcda2de38c33446bcb3e7a27a2
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2020
ms.locfileid: "88983315"
---
# <a name="sortorder-property-adox"></a>Свойство SortOrder (ADOX)
Указывает последовательность сортировки для столбца (только столбцы индекса).  
  
## <a name="settings-and-return-values"></a>Параметры и возвращаемые значения  
 Задает и возвращает значение **типа Long** , которое может быть одной из констант [сортордеренум](./sortorderenum.md) . Значение по умолчанию — **адсортасцендинг**.  
  
## <a name="remarks"></a>Remarks  
 Это свойство применяется только к объектам [столбцов](./column-object-adox.md) в коллекции [Columns](./columns-collection-adox.md) [индекса](./index-object-adox.md).  
  
## <a name="applies-to"></a>Применение  
 [Объект Column (ADOX)](./column-object-adox.md)  
  
## <a name="see-also"></a>См. также  
 [Пример свойства SortOrder (Visual Basic)](./sortorder-property-example-vb.md)   
 [Коллекция Columns (ADOX)](./columns-collection-adox.md)   
 [Объект Index (ADOX)](./index-object-adox.md)