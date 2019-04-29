---
title: Изменить форму имени свойства (динамическое) (ADO) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- Reshape Name property [ADO]
ms.assetid: 690229d1-46cc-42e6-a57d-4438251fe248
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 6a07ec878b1198fbf23bfb251460d83869313c83
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63062132"
---
# <a name="reshape-name-property-dynamic-ado"></a>Свойство Reshape Name (динамическое) (ADO)
Указывает имя для [записей](../../../ado/reference/ado-api/recordset-object-ado.md) объекта.  
  
## <a name="return-values"></a>Возвращаемые значения  
 Возвращает **строка** значение, которое является имя **записей**.  
  
## <a name="remarks"></a>Примечания  
 Имена сохраняются во время подключения или до **записей** закрыт.  
  
 **Изменить форму имени** свойство предназначено для использования с функцией повторного формирования [службы Microsoft Data Shaping Service для OLE DB](../../../ado/guide/appendixes/microsoft-data-shaping-service-for-ole-db-ado-service-provider.md) поставщика услуг. Имена должны быть уникальными для участия в повторного формирования.  
  
 Это свойство только для чтения, однако его можно установить косвенно при **записей** создается. Например, если выражение фигуру, команда создает **записей** и присваивает ему имя псевдонима с помощью **AS** ключевое слово, псевдоним назначается **изменить форму имени** свойство. Если псевдоним не был объявлен, **изменить форму имени** присваивается уникальное имя, созданное функцией службы формирования данных. Если псевдоним совпадает с именем существующего **записей**, ни **записей** форму можно изменить, пока не освобождается один из них. Поведение по умолчанию можно изменить, задав уникальное имя [изменить форму имени](../../../ado/reference/ado-api/reshape-name-property-dynamic-ado.md) свойство соединения ADO для **True**. Задание этого свойства дает формирования разрешение службы, чтобы изменить имя пользователя, при необходимости, чтобы обеспечить уникальность данных. Дополнительные сведения о изменение формы, см. в разделе [службы Microsoft Data Shaping Service для OLE DB (ADO поставщиком услуг)](../../../ado/guide/appendixes/microsoft-data-shaping-service-for-ole-db-ado-service-provider.md).  
  
 Используйте **изменить форму имени** свойства, если вы хотите указывать **записей** в команде фигуры, или если вы не знаете имя так как он был создан службой формирования данных. В этом случае можно либо создать команду ФИГУРЫ путем объединения команда вокруг строкой, возвращенной **изменить форму имени** свойство.  
  
 **Изменить имя** динамическое свойство добавляется к **записей** объекта [свойства](../../../ado/reference/ado-api/properties-collection-ado.md) коллекции при [CursorLocation](../../../ado/reference/ado-api/cursorlocation-property-ado.md) свойству **adUseClient**.  
  
## <a name="applies-to"></a>Объект применения  
 [Объект Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>См. также  
 [Служба для OLE DB (ADO поставщиком услуг) формирования данных](../../../ado/guide/appendixes/microsoft-data-shaping-service-for-ole-db-ado-service-provider.md)   
 [Общие сведения о командах фигуры](../../../ado/guide/data/shape-commands-in-general.md)   
 [Объект Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)
