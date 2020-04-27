---
title: Свойство "имя формы" — Dynamic (ADO) | Документация Майкрософт
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
ms.openlocfilehash: ec72b2b1908f967caee4610e27315acaab787ac9
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "67917171"
---
# <a name="reshape-name-property-dynamic-ado"></a>Свойство Reshape Name (динамическое) (ADO)
Задает имя объекта [набора записей](../../../ado/reference/ado-api/recordset-object-ado.md) .  
  
## <a name="return-values"></a>Возвращаемые значения  
 Возвращает **строковое** значение, которое является именем **набора записей**.  
  
## <a name="remarks"></a>Remarks  
 Имена сохраняются в течение соединения или до закрытия **набора записей** .  
  
 Свойство **изменить имя формы** в основном предназначено для использования с функцией изменения формы [службы формирования данных (Майкрософт) для](../../../ado/guide/appendixes/microsoft-data-shaping-service-for-ole-db-ado-service-provider.md) поставщика служб OLE DB. Имена должны быть уникальными для участия в повторной формировании.  
  
 Это свойство доступно только для чтения, но может быть задано косвенно при создании **набора записей** . Например, если предложение команды Shape создает **набор записей** и присваивает ему имя псевдонима с помощью ключевого слова **as** , псевдоним присваивается свойству **Name Shape** . Если псевдоним не объявлен, свойству " **имя перерисовки** " присваивается уникальное имя, созданное службой формирования данных. Если имя псевдонима совпадает с именем существующего **набора записей**, ни один из **наборов записей** не может быть переустановлен до тех пор, пока не будет освобожден. Поведение по умолчанию можно изменить, задав уникальное имя в свойстве [изменить имя формы](../../../ado/reference/ado-api/reshape-name-property-dynamic-ado.md) в соединении ADO со значением **true**. Задание этого свойства дает службе формирования данных разрешение на изменение имени, назначенного пользователю, при необходимости для обеспечения уникальности. Дополнительные сведения об изменении формы см. в разделе [Служба формирования данных Майкрософт для OLE DB (поставщик служб ADO)](../../../ado/guide/appendixes/microsoft-data-shaping-service-for-ole-db-ado-service-provider.md).  
  
 Свойство **изменить имя формы** используется, если необходимо сослаться на **набор записей** в команде Shape или если имя неизвестно, поскольку оно было создано службой формирования данных. В этом случае можно создать команду SHAPE, объединив команду со строкой, возвращаемой свойством « **имя формы** ».  
  
 **Перерисовка имени** — это динамическое свойство, добавленное к коллекции [свойств](../../../ado/reference/ado-api/properties-collection-ado.md) объекта **Recordset** , если свойство [CursorLocation](../../../ado/reference/ado-api/cursorlocation-property-ado.md) имеет значение **адусеклиент**.  
  
## <a name="applies-to"></a>Применяется к  
 [Объект Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>См. также  
 [Служба формирования данных Майкрософт для OLE DB (поставщик служб ADO)](../../../ado/guide/appendixes/microsoft-data-shaping-service-for-ole-db-ado-service-provider.md)   
 [Общие команды формы](../../../ado/guide/data/shape-commands-in-general.md)   
 [Объект Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)
