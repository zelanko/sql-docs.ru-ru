---
title: Использование ADO с ADO MD | Документация Майкрософт
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 69707e5026497a1f98ab168d71b4e6b286520fbe
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47790428"
---
# <a name="using-ado-with-ado-md"></a>Использование ADO с объектами данных ActiveX (MD)
ADO и ADO MD, связанных, но отдельных объектные модели. ADO предоставляет объекты для соединения с источниками данных, выполнения команд, получение табличных данных и схемы метаданных в табличном формате и просматривать сведения об ошибке поставщика. Многомерные Объекты ADO предоставляет объекты для получения многомерных данных и просмотр метаданных многомерной схемой.  
  
 При работе с MDP, вы можете использовать ADO, ADO MD или оба вместе с приложением. Ссылаясь на обе библиотеки в проекте, будет иметь полный доступ к функциональных возможностях, предоставляемых вашей MDP.  
  
 Часто полезно для потребителей получить представление плоского, табличных многомерного набора данных. Это можно сделать с помощью ADO [записей](../../../ado/reference/ado-api/recordset-object-ado.md) объекта. Указать источник для вашей [набора ячеек](../../../ado/reference/ado-md-api/cellset-object-ado-md.md) как ***источника*** параметр для [откройте](../../../ado/reference/ado-api/open-method-ado-recordset.md) метод **записей**, а не как источник ADO MD **Cellset**.  
  
 Также может быть полезно просмотреть метаданные схемы в табличное представление, а не в виде иерархии объектов. ADO [OpenSchema](../../../ado/reference/ado-api/openschema-method.md) метод [подключения](../../../ado/reference/ado-api/connection-object-ado.md) объект позволит пользователю открывать **записей** , содержащий сведения о схеме. ***QueryType*** параметр **OpenSchema** метод имеет несколько [SchemaEnum](../../../ado/reference/ado-api/schemaenum.md) значений, связанных с MDPs. Эти значения определяются следующим образом:  
  
-   **adSchemaCubes**  
  
-   **adSchemaDimensions**  
  
-   **adSchemaHierarchies**  
  
-   **adSchemaLevels**  
  
-   **adSchemaMeasures**  
  
-   **adSchemaMembers**  
  
 Для использования значений перечисления ADO с ADO MD свойствами или методами, проект должен ссылаться на библиотеки ADO и многомерные Объекты ADO. Например, можно использовать ADO **adState** значений перечисления, с помощью ADO MD [состояние](../../../ado/reference/ado-md-api/state-property-ado-md.md) свойство. Дополнительные сведения о том, как установить ссылки на библиотеки см. в документации средства разработки.  
  
 Дополнительные сведения о объектов ADO и методов, см. в разделе [Справочник по API ADO](../../../ado/reference/ado-api/ado-api-reference.md).  
  
## <a name="see-also"></a>См. также  
 [Объектная модель ADO MD](../../../ado/reference/ado-md-api/ado-md-object-model.md)   
 [ADO (многомерные данные) (многомерные Объекты ADO)](../../../ado/guide/multidimensional/ado-multidimensional-ado-md.md)   
 [Общие сведения о многомерных схемах и данных](../../../ado/guide/multidimensional/overview-of-multidimensional-schemas-and-data.md)   
 [Программирование с использованием ADO MD](../../../ado/guide/multidimensional/programming-with-ado-md.md)   
 [Работа с многомерными данными](../../../ado/guide/multidimensional/working-with-multidimensional-data.md)
