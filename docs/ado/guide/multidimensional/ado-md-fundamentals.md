---
title: Основные принципы ADO MD | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 02/15/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- ADO MD, fundamentals
ms.assetid: f6a20d9f-c1ab-474c-b9f3-82277e2a126d
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: bbff704e174dd824eca7b1f71c8f9d3fc15def51
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "66704412"
---
# <a name="ado-md-fundamentals"></a>Основные принципы объектов данных ActiveX (MD)
Microsoft® ActiveX® Data Objects (многомерные выражения) (многомерные Объекты ADO) обеспечивает простой доступ к многомерным данным из языков, таких как Microsoft Visual Basic®, Microsoft Visual C++®. ADO MD расширяет Microsoft ActiveX® Data Objects (ADO) для включения объекты, относящиеся к многомерным данным, например [CubeDef](../../../ado/reference/ado-md-api/cubedef-object-ado-md.md) и [Cellset](../../../ado/reference/ado-md-api/cellset-object-ado-md.md) объектов. С ADO MD Обзор многомерной схемой, запроса куба и получения результатов.  
  
 Как и ADO ADO MD использует поставщика OLE DB для получения доступа к данным. Для работы с ADO MD, поставщик должен быть поставщик многомерных данных (MDP), согласно спецификации OLE DB для OLAP. MDP представляет данные в многомерных представлений вместо табличных представлениях, в это как поставщик табличных данных (TDP) представляет данные. См. в документации по поставщику OLE DB для OLAP, Дополнительные сведения о конкретных синтаксисом и поведением, поддерживаемых поставщиком.  
  
 В этом документе предполагается знание языка программирования Visual Basic и общие знания ADO и OLAP. Дополнительные сведения см. в разделе [руководство по программированию объектов ADO](../../../ado/guide/ado-programmer-s-guide.md) и [OLE DB для оперативной аналитической обработки (OLAP)](https://msdn.microsoft.com/library/windows/desktop/ms717005.aspx).  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Общие сведения о многомерных схемах и данных](../../../ado/guide/multidimensional/overview-of-multidimensional-schemas-and-data.md)  
  
-   [Работа с многомерными данными](../../../ado/guide/multidimensional/working-with-multidimensional-data.md)  
  
-   [Использование ADO с объектами данных ActiveX (MD)](../../../ado/guide/multidimensional/using-ado-with-ado-md.md)  
  
-   [Программирование с объектами данных ActiveX (MD)](../../../ado/guide/multidimensional/programming-with-ado-md.md)  
  
## <a name="see-also"></a>См. также  
 [Объектная модель ADO MD](../../../ado/reference/ado-md-api/ado-md-object-model.md)   
 [Руководство по программированию объектов ADO](../../../ado/guide/ado-programmer-s-guide.md)   
 [Расширения ADO для языка определения данных и безопасности (ADOX)](../../../ado/guide/extensions/ado-extensions-for-data-definition-language-and-security-adox.md)   
 [Общие сведения о многомерных схемах и данных](../../../ado/guide/multidimensional/overview-of-multidimensional-schemas-and-data.md)   
 [Программирование с использованием ADO MD](../../../ado/guide/multidimensional/programming-with-ado-md.md)   
 [Использование ADO с ADO MD](../../../ado/guide/multidimensional/using-ado-with-ado-md.md)   
 [Работа с многомерными данными](../../../ado/guide/multidimensional/working-with-multidimensional-data.md)
