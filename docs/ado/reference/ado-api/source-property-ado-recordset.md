---
title: Свойство (объект Recordset ADO) источника | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset15::putref_Source
- Recordset15::Source
- Recordset15::PutSource
- Recordset15::get_Source
- Recordset15::GetSource
- Recordset15::PutRefSource
- Recordset15::put_Source
helpviewer_keywords:
- Source property [ADO Recordset]
ms.assetid: a05ba2c9-2821-4343-8607-4de9b764ec91
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 718124fce3c2ce7a1adf9e6dbdb1d54e8a834fca
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62740374"
---
# <a name="source-property-ado-recordset"></a>Свойство Source (объект Recordset ADO)
Указывает источник данных для [записей](../../../ado/reference/ado-api/recordset-object-ado.md) объекта.  
  
## <a name="settings-and-return-values"></a>Параметры и возвращаемые значения  
 Наборы **строка** значение или [команда](../../../ado/reference/ado-api/command-object-ado.md) ссылка; возвращает только **строка** значение, указывающее источник **записей**.  
  
## <a name="remarks"></a>Примечания  
 Используйте **источника** свойство, чтобы указать источник данных для **записей** объекта с помощью одного из следующих: **команда** объектов переменной, инструкции SQL, хранимая процедура, или имени таблицы.  
  
 Если задать **источника** свойства **команда** объекта, [ActiveConnection](../../../ado/reference/ado-api/activeconnection-property-ado.md) свойство **записей** объект будет наследовать значение **ActiveConnection** свойство для указанного **команда** объекта. Тем не менее, чтение **источника** свойство не возвращает **команда** ; вместо этого он возвращает [CommandText](../../../ado/reference/ado-api/commandtext-property-ado.md) свойство **команда** объекта, для которых **источника** свойство.  
  
 Если **источника** свойство является инструкции SQL, хранимой процедуры или имя таблицы, можно оптимизировать производительность, передав соответствующий *параметры* аргумент с [откройте](../../../ado/reference/ado-api/open-method-ado-recordset.md)вызов метода.  
  
 **Источника** свойство доступно для чтения/записи для закрыто **записей** объектов и только для чтения для открытой **записей** объектов.  
  
## <a name="applies-to"></a>Объект применения  
 [Объект Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>См. также  
 [Пример свойства Source (Visual Basic)](../../../ado/reference/ado-api/source-property-example-vb.md)   
 [Свойство Source (объект Error ADO)](../../../ado/reference/ado-api/source-property-ado-error.md)   
 [Свойство Source (объект Record ADO)](../../../ado/reference/ado-api/source-property-ado-record.md)
