---
description: Использование ADO с объектами данных ActiveX (MD)
title: Использование ADO с объекты данных ActiveX (MD) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- ADO, using with ADO MD
ms.assetid: cfae435e-2ac3-4312-8c1e-9ca4a74cd875
author: rothja
ms.author: jroth
ms.openlocfilehash: 6314ae9a0682e1c10b1ecd45c8f8d5217e7d6426
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88452406"
---
# <a name="using-ado-with-ado-md"></a>Использование ADO с объектами данных ActiveX (MD)
ADO и объекты данных ActiveX (MD) являются взаимосвязанными, но отдельными объектными моделями. ADO предоставляет объекты для подключения к источникам данных, исполнения команд, получения табличных данных и метаданных схемы в табличном формате и просмотра сведений об ошибках поставщика. Объекты данных ActiveX (MD) предоставляет объекты для извлечения многомерных данных и просмотра метаданных многомерной схемы.  
  
 При работе с MDP можно выбрать использование ADO, объекты данных ActiveX (MD) или и того, и другого в приложении. Ссылаясь на обе библиотеки в проекте, вы получите полный доступ к функциональным возможностям, предоставляемым вашим MDP.  
  
 Для потребителей часто бывает удобно получать плоское табличное представление многомерного набора данных. Это можно сделать с помощью объекта [набора записей](../../../ado/reference/ado-api/recordset-object-ado.md) ADO. Укажите источник для набора [ячеек](../../../ado/reference/ado-md-api/cellset-object-ado-md.md) в качестве ***исходного*** параметра для метода [Open](../../../ado/reference/ado-api/open-method-ado-recordset.md) в **наборе записей**, а не **источника объекты данных ActiveX (MD).**  
  
 Также может быть полезно просматривать метаданные схемы в табличном представлении, а не в виде иерархии объектов. Метод ADO [OpenSchema](../../../ado/reference/ado-api/openschema-method.md) объекта [Connection](../../../ado/reference/ado-api/connection-object-ado.md) позволяет пользователю открыть **набор записей** , содержащий сведения о схеме. Параметр ***QueryType*** метода **OpenSchema** имеет несколько значений [SchemaEnum](../../../ado/reference/ado-api/schemaenum.md) , относящихся специально к мдпс. Это такие значения:  
  
-   **адсчемакубес**  
  
-   **адсчемадименсионс**  
  
-   **adSchemaHierarchies**  
  
-   **adSchemaLevels**  
  
-   **адсчемамеасурес**  
  
-   **adSchemaMembers**  
  
 Чтобы использовать значения перечисления ADO с объекты данных ActiveX (MD) свойствами или методами, проект должен ссылаться на библиотеки ADO и объекты данных ActiveX (MD). Например, можно использовать значения перечисления ADO **адстате** со свойством [State](../../../ado/reference/ado-md-api/state-property-ado-md.md) объекты данных ActiveX (MD). Дополнительные сведения о том, как устанавливать ссылки на библиотеки, см. в документации по средству разработки.  
  
 Дополнительные сведения об объектах и методах ADO см. в [справочнике по API ADO](../../../ado/reference/ado-api/ado-api-reference.md).  
  
## <a name="see-also"></a>См. также:  
 [Объектная модель объекты данных ActiveX (MD)](../../../ado/reference/ado-md-api/ado-md-object-model.md)   
 [ADO (многомерные) (объекты данных ActiveX (MD))](../../../ado/guide/multidimensional/ado-multidimensional-ado-md.md)   
 [Общие сведения о многомерных схемах и данных](../../../ado/guide/multidimensional/overview-of-multidimensional-schemas-and-data.md)   
 [Программирование с помощью объекты данных ActiveX (MD)](../../../ado/guide/multidimensional/programming-with-ado-md.md)   
 [Работа с многомерными данными](../../../ado/guide/multidimensional/working-with-multidimensional-data.md)
