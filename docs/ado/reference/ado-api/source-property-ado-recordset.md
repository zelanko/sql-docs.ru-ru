---
title: "Исходное свойство (набора записей ADO) | Документы Microsoft"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- Recordset15::putref_Source
- Recordset15::Source
- Recordset15::PutSource
- Recordset15::get_Source
- Recordset15::GetSource
- Recordset15::PutRefSource
- Recordset15::put_Source
helpviewer_keywords: Source property [ADO Recordset]
ms.assetid: a05ba2c9-2821-4343-8607-4de9b764ec91
caps.latest.revision: "11"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 36180bafb53d72985c2dc671d80147c8ffaa8588
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="source-property-ado-recordset"></a>Свойство Source (набора записей ADO)
Указывает источник данных для [записей](../../../ado/reference/ado-api/recordset-object-ado.md) объекта.  
  
## <a name="settings-and-return-values"></a>Параметры и возвращаемые значения  
 Наборы **строка** значение или [команда](../../../ado/reference/ado-api/command-object-ado.md) объекта ссылки; возвращает только **строка** значение, указывающее источник **записей**.  
  
## <a name="remarks"></a>Замечания  
 Используйте **источника** свойство, чтобы указать источник данных для **записей** с помощью одного из следующих действий: **команда** объекта переменной, инструкции SQL, хранимая процедура, или имя таблицы.  
  
 Если задать **источника** свойства **команды** объекта, [ActiveConnection](../../../ado/reference/ado-api/activeconnection-property-ado.md) свойство **записей** объект будет наследовать значение **ActiveConnection** свойства для указанного **команда** объекта. Тем не менее, чтении **источника** свойство не возвращает **команда** объекта; вместо этого он возвращает [CommandText](../../../ado/reference/ado-api/commandtext-property-ado.md) свойство **команда** объект, который позволяет определить **источника** свойство.  
  
 Если **источника** свойство является инструкции SQL, хранимой процедуры или имя таблицы, можно оптимизировать производительность путем передачи соответствующего *параметры* аргумент с [откройте](../../../ado/reference/ado-api/open-method-ado-recordset.md)вызова метода.  
  
 **Источника** свойство является чтение и запись для закрытия **записей** объектов и только для чтения для открытия **записей** объектов.  
  
## <a name="applies-to"></a>Объект применения  
 [Объект Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>См. также:  
 [Пример свойства источника (Visual Basic)](../../../ado/reference/ado-api/source-property-example-vb.md)   
 [Свойство Source (ошибка)](../../../ado/reference/ado-api/source-property-ado-error.md)   
 [Свойство Source (объект Record ADO)](../../../ado/reference/ado-api/source-property-ado-record.md)
