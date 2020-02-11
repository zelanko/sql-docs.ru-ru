---
title: Основы объекты данных ActiveX (MD) | Документация Майкрософт
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
ms.openlocfilehash: 690c7b58c336596485b9ade77f0c02928853cd2d
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "67923202"
---
# <a name="ado-md-fundamentals"></a>Основные принципы объектов данных ActiveX (MD)
Microsoft®® ActiveX Data Objects (объекты данных ActiveX (MD)) предоставляет простой доступ к многомерным данным на таких языках, как Microsoft Visual Basic®, Microsoft Visual C++®. Объекты данных ActiveX (MD) расширяет Microsoft ActiveX® объекты данных (ADO) для включения объектов, характерных для многомерных данных, таких как объекты [CubeDef](../../../ado/reference/ado-md-api/cubedef-object-ado-md.md) и набор [ячеек](../../../ado/reference/ado-md-api/cellset-object-ado-md.md) . С помощью объекты данных ActiveX (MD) можно просматривать многомерную схему, выполнять запросы к кубу и получать результаты.  
  
 Как и ADO, объекты данных ActiveX (MD) использует базовый поставщик OLE DB для получения доступа к данным. Для работы с объекты данных ActiveX (MD) поставщик должен быть многомерным поставщиком данных (MDP), как определено OLE DB для спецификации OLAP. MDP представляет данные в многомерных представлениях вместо табличных представлений, то есть как поставщик табличных данных (TDP) представляет данные. Дополнительные сведения о синтаксисе и характере, поддерживаемом поставщиком, см. в документации по поставщику OLE DB OLAP.  
  
 В этом документе предполагается, что у вас есть опыт работы с Visual Basic языком программирования и общие знания ADO и OLAP. Дополнительные сведения см. в документации [программиста по ADO](../../../ado/guide/ado-programmer-s-guide.md) и [OLE DB для оперативной аналитической обработки (OLAP)](https://msdn.microsoft.com/library/windows/desktop/ms717005.aspx).  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Общие сведения о многомерных схемах и данных](../../../ado/guide/multidimensional/overview-of-multidimensional-schemas-and-data.md)  
  
-   [Работа с многомерными данными](../../../ado/guide/multidimensional/working-with-multidimensional-data.md)  
  
-   [Использование ADO с объектами данных ActiveX (MD)](../../../ado/guide/multidimensional/using-ado-with-ado-md.md)  
  
-   [Программирование с объектами данных ActiveX (MD)](../../../ado/guide/multidimensional/programming-with-ado-md.md)  
  
## <a name="see-also"></a>См. также:  
 [Объектная модель объекты данных ActiveX (MD)](../../../ado/reference/ado-md-api/ado-md-object-model.md)   
 [Руководством программиста по ADO](../../../ado/guide/ado-programmer-s-guide.md)   
 [Расширения ADO для языка описания данных и системы безопасности (ADOX)](../../../ado/guide/extensions/ado-extensions-for-data-definition-language-and-security-adox.md)   
 [Общие сведения о многомерных схемах и данных](../../../ado/guide/multidimensional/overview-of-multidimensional-schemas-and-data.md)   
 [Программирование с помощью объекты данных ActiveX (MD)](../../../ado/guide/multidimensional/programming-with-ado-md.md)   
 [Использование ADO с объекты данных ActiveX (MD)](../../../ado/guide/multidimensional/using-ado-with-ado-md.md)   
 [Работа с многомерными данными](../../../ado/guide/multidimensional/working-with-multidimensional-data.md)
