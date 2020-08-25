---
description: Свойство CommandStream (ADO)
title: Свойство CommandStream (ADO) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Command::CommandStream
helpviewer_keywords:
- CommandStream property [ADO]
ms.assetid: f78f61b6-87e0-48dc-961e-83d0e20da58e
author: rothja
ms.author: jroth
ms.openlocfilehash: 20b52a91429e2db6478aab36f2db5928bc2d30f5
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/24/2020
ms.locfileid: "88776153"
---
# <a name="commandstream-property-ado"></a>Свойство CommandStream (ADO)
Указывает поток, используемый в качестве входных данных для объекта [команды](./command-object-ado.md) .  
  
## <a name="settings-and-return-values"></a>Параметры и возвращаемые значения  
 Задает или возвращает поток, используемый в качестве входных данных для объекта **команды** . Формат этого потока зависит от поставщика. Дополнительные сведения см. в документации поставщика. Это свойство аналогично свойству [CommandText](./commandtext-property-ado.md) , которое используется для указания строки для входных данных **команды**.  
  
## <a name="remarks"></a>Remarks  
 **CommandStream** и **CommandText** являются взаимоисключающими. Когда пользователь задает свойство **CommandStream** , свойству **CommandText** присваивается пустая строка (""). Если пользователь задает свойство **CommandText** , свойству **CommandStream** будет присвоено значение **Nothing**.  
  
 Поведение методов **Command. parameters. Refresh** и **Command. Prepare** определяется поставщиком. Значения параметров в потоке не могут быть обновлены.  
  
 Входной поток недоступен для других объектов ADO, возвращающих источник **команды**. Например, если [источнику](./source-property-ado-recordset.md) [набора записей](./recordset-object-ado.md) присваивается объект **Command** , имеющий поток в качестве входных данных, то **набор записей. Source** продолжит возвращать свойство **CommandText** , которое содержит пустую строку (""), а не содержимое потока свойства **CommandStream** .  
  
 При использовании потока команд (как указано в **CommandStream**) единственными допустимыми значениями [Коммандтипинум](./commandtypeenum.md) для свойства [CommandType](./commandtype-property-ado.md) являются **адкмдтекст** и **адкмдункновн**. Любое другое значение приводит к возникновению ошибки.  
  
## <a name="applies-to"></a>Применение  
 [Объект Command (ADO)](./command-object-ado.md)  
  
## <a name="see-also"></a>См. также  
 [Свойство CommandText (ADO)](./commandtext-property-ado.md)   
 [Свойство диалекта](./dialect-property.md)   
 [CommandTypeEnum](./commandtypeenum.md)