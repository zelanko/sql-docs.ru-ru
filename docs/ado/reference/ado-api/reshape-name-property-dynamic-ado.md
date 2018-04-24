---
title: Изменить имя свойства динамические (ADO) | Документы Microsoft
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- Reshape Name property [ADO]
ms.assetid: 690229d1-46cc-42e6-a57d-4438251fe248
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 8a1d81e91edfcab8b6938f5898ae4fd46cc38b67
ms.sourcegitcommit: bb044a48a6af9b9d8edb178dc8c8bd5658b9ff68
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2018
---
# <a name="reshape-name-property-dynamic-ado"></a>Изменить имя свойства динамические (ADO)
Указывает имя для [записей](../../../ado/reference/ado-api/recordset-object-ado.md) объекта.  
  
## <a name="return-values"></a>Возвращаемые значения  
 Возвращает **строка** значение, представляющее имя **записей**.  
  
## <a name="remarks"></a>Замечания  
 Имена сохраняются во время соединения, или пока не **записей** закрыт.  
  
 **Изменить имя** свойство предназначено для использования с функцией повторного формирования [службы Microsoft Data Shaping Service для OLE DB](../../../ado/guide/appendixes/microsoft-data-shaping-service-for-ole-db-ado-service-provider.md) поставщика услуг. Имена должны быть уникальными для участия в повторного формирования.  
  
 Это свойство доступно только для чтения, но можно задать косвенно при **записей** создается. Например, если предложение фигуру, команда создает **записей** и присваивает ему имя псевдонима с помощью **AS** ключевое слово, присваивается псевдоним **изменить имя** свойства. Если псевдоним не был объявлен, **изменить имя** присваивается уникальное имя, созданное службой формирования данных. Если псевдоним совпадает с именем существующего **записей**, ни **записей** форму можно изменить пока один из них не будет освобождена. Поведение по умолчанию можно изменить, задав уникальное имя [изменить имя](../../../ado/reference/ado-api/reshape-name-property-dynamic-ado.md) свойство соединения ADO для **True**. Задание этого свойства позволяет формирования службы разрешение на изменение имени пользователя, назначенного при необходимости для обеспечения уникальности данных. Дополнительные сведения об изменении см. в разделе [службы Microsoft Data Shaping Service для OLE DB (ADO поставщиком услуг)](../../../ado/guide/appendixes/microsoft-data-shaping-service-for-ole-db-ado-service-provider.md).  
  
 Используйте **изменить имя** свойства, если вы хотите указывать **записей** в команде фигуры или если вы не знаете имя, поскольку оно было создано службой формирования данных. В этом случае можно создать команду ФИГУРЫ путем объединения команды вокруг строку, возвращаемую **изменить имя** свойства.  
  
 **Изменить имя** динамическое свойство добавляется к **записей** объекта [свойства](../../../ado/reference/ado-api/properties-collection-ado.md) коллекции при [CursorLocation](../../../ado/reference/ado-api/cursorlocation-property-ado.md) свойству **adUseClient**.  
  
## <a name="applies-to"></a>Объект применения  
 [Объект Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>См. также  
 [Microsoft службы формирования данных для OLE DB (ADO поставщиком услуг)](../../../ado/guide/appendixes/microsoft-data-shaping-service-for-ole-db-ado-service-provider.md)   
 [Команды фигуры в целом](../../../ado/guide/data/shape-commands-in-general.md)   
 [Объект Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)
