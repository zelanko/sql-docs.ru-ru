---
description: Основные принципы объектов данных ActiveX (MD)
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
author: rothja
ms.author: jroth
ms.openlocfilehash: eb14a1b97ba6670b2170021bc354890b41fa01ca
ms.sourcegitcommit: c4d564435c008e2c92035efd2658172f20f07b2b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/24/2020
ms.locfileid: "88758794"
---
# <a name="ado-md-fundamentals"></a>Основные принципы объектов данных ActiveX (MD)
Microsoft®® ActiveX Data Objects (объекты данных ActiveX (MD)) предоставляет простой доступ к многомерным данным на таких языках, как Microsoft Visual Basic®, Microsoft Visual C++®. Объекты данных ActiveX (MD) расширяет Microsoft ActiveX® объекты данных (ADO) для включения объектов, характерных для многомерных данных, таких как объекты [CubeDef](../../reference/ado-md-api/cubedef-object-ado-md.md) и набор [ячеек](../../reference/ado-md-api/cellset-object-ado-md.md) . С помощью объекты данных ActiveX (MD) можно просматривать многомерную схему, выполнять запросы к кубу и получать результаты.  
  
 Как и ADO, объекты данных ActiveX (MD) использует базовый поставщик OLE DB для получения доступа к данным. Для работы с объекты данных ActiveX (MD) поставщик должен быть многомерным поставщиком данных (MDP), как определено OLE DB для спецификации OLAP. MDP представляет данные в многомерных представлениях вместо табличных представлений, то есть как поставщик табличных данных (TDP) представляет данные. Дополнительные сведения о синтаксисе и характере, поддерживаемом поставщиком, см. в документации по поставщику OLE DB OLAP.  
  
 В этом документе предполагается, что у вас есть опыт работы с Visual Basic языком программирования и общие знания ADO и OLAP. Дополнительные сведения см. в документации [программиста по ADO](../ado-programmer-s-guide.md) и [OLE DB для оперативной аналитической обработки (OLAP)](/previous-versions/windows/desktop/ms717005(v=vs.85)).  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Общие сведения о многомерных схемах и данных](./overview-of-multidimensional-schemas-and-data.md)  
  
-   [Работа с многомерными данными](./working-with-multidimensional-data.md)  
  
-   [Использование ADO с объектами данных ActiveX (MD)](./using-ado-with-ado-md.md)  
  
-   [Программирование с объектами данных ActiveX (MD)](./programming-with-ado-md.md)  
  
## <a name="see-also"></a>См. также  
 [Объектная модель объекты данных ActiveX (MD)](../../reference/ado-md-api/ado-md-object-model.md)   
 [Руководством программиста по ADO](../ado-programmer-s-guide.md)   
 [Расширения ADO для языка описания данных и системы безопасности (ADOX)](../extensions/ado-extensions-for-data-definition-language-and-security-adox.md)   
 [Общие сведения о многомерных схемах и данных](./overview-of-multidimensional-schemas-and-data.md)   
 [Программирование с помощью объекты данных ActiveX (MD)](./programming-with-ado-md.md)   
 [Использование ADO с объекты данных ActiveX (MD)](./using-ado-with-ado-md.md)   
 [Работа с многомерными данными](./working-with-multidimensional-data.md)