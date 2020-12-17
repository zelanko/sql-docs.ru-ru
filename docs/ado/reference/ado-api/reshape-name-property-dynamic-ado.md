---
description: Свойство Reshape Name (динамическое) (ADO)
title: Изменение имени Property-Dynamic (ADO) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- Reshape Name property [ADO]
ms.assetid: 690229d1-46cc-42e6-a57d-4438251fe248
author: rothja
ms.author: jroth
ms.openlocfilehash: 1678bcbae00c7d1022bfeffbb72a3e9b1ee63401
ms.sourcegitcommit: 370cab80fba17c15fb0bceed9f80cb099017e000
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/17/2020
ms.locfileid: "97637981"
---
# <a name="reshape-name-property-dynamic-ado"></a>Свойство Reshape Name (динамическое) (ADO)
Задает имя объекта [набора записей](./recordset-object-ado.md) .  
  
## <a name="return-values"></a>Возвращаемые значения  
 Возвращает **строковое** значение, которое является именем **набора записей**.  
  
## <a name="remarks"></a>Комментарии  
 Имена сохраняются в течение соединения или до закрытия **набора записей** .  
  
 Свойство **изменить имя формы** в основном предназначено для использования с функцией изменения формы [службы формирования данных (Майкрософт) для](../../guide/appendixes/microsoft-data-shaping-service-for-ole-db-ado-service-provider.md) поставщика служб OLE DB. Имена должны быть уникальными для участия в повторной формировании.  
  
 Это свойство доступно только для чтения, но может быть задано косвенно при создании **набора записей** . Например, если предложение команды Shape создает **набор записей** и присваивает ему имя псевдонима с помощью ключевого слова **as** , псевдоним присваивается свойству **Name Shape** . Если псевдоним не объявлен, свойству " **имя перерисовки** " присваивается уникальное имя, созданное службой формирования данных. Если имя псевдонима совпадает с именем существующего **набора записей**, ни один из **наборов записей** не может быть переустановлен до тех пор, пока не будет освобожден. Поведение по умолчанию можно изменить, задав уникальное имя в свойстве **изменить имя формы** в соединении ADO со значением **true**. Задание этого свойства дает службе формирования данных разрешение на изменение имени, назначенного пользователю, при необходимости для обеспечения уникальности. Дополнительные сведения об изменении формы см. в разделе [Служба формирования данных Майкрософт для OLE DB (поставщик служб ADO)](../../guide/appendixes/microsoft-data-shaping-service-for-ole-db-ado-service-provider.md).  
  
 Свойство **изменить имя формы** используется, если необходимо сослаться на **набор записей** в команде Shape или если имя неизвестно, поскольку оно было создано службой формирования данных. В этом случае можно создать команду SHAPE, объединив команду со строкой, возвращаемой свойством « **имя формы** ».  
  
 **Перерисовка имени** — это динамическое свойство, добавленное к коллекции [свойств](./properties-collection-ado.md) объекта **Recordset** , если свойство [CursorLocation](./cursorlocation-property-ado.md) имеет значение **адусеклиент**.  
  
## <a name="applies-to"></a>Применение  
 [Объект Recordset (ADO)](./recordset-object-ado.md)  
  
## <a name="see-also"></a>См. также:  
 [Служба формирования данных Майкрософт для OLE DB (поставщик служб ADO)](../../guide/appendixes/microsoft-data-shaping-service-for-ole-db-ado-service-provider.md)   
 [Общие команды формы](../../guide/data/shape-commands-in-general.md)   
 [Объект Recordset (ADO)](./recordset-object-ado.md)