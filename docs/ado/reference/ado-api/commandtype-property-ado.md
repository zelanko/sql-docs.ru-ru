---
title: Свойство CommandType (ADO) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Command15::CommandType
helpviewer_keywords:
- CommandType property [ADO]
ms.assetid: ca44809c-8647-48b6-a7fb-0be70a02f53e
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 5fde8adfb1b3f78e8dd0d047f8b100ddada4608c
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "66698682"
---
# <a name="commandtype-property-ado"></a>Свойство CommandType (ADO)
Указывает тип [команда](../../../ado/reference/ado-api/command-object-ado.md) объекта.  
  
## <a name="settings-and-return-values"></a>Параметры и возвращаемые значения  
 Задает или возвращает один или несколько [CommandTypeEnum](../../../ado/reference/ado-api/commandtypeenum.md) значения.  
  
> [!NOTE]
>  Не используйте **CommandTypeEnum** значения **adCmdFile** или **adCmdTableDirect** с **CommandType**. Эти значения могут использоваться только как параметры с [откройте](../../../ado/reference/ado-api/open-method-ado-recordset.md) и [Requery](../../../ado/reference/ado-api/requery-method.md) методы [записей](../../../ado/reference/ado-api/recordset-object-ado.md).  
  
## <a name="remarks"></a>Примечания  
 Используйте **CommandType** свойство, чтобы оптимизировать вычисление [CommandText](../../../ado/reference/ado-api/commandtext-property-ado.md) свойство.  
  
 Если **CommandType** свойству будет присвоено значение по умолчанию, **adCmdUnknown**, могут возникнуть снижение производительности, так как ADO необходимо выполнять вызовы к поставщику для определения  **CommandText** свойство является инструкции SQL, хранимой процедуры или имя таблицы. Если вы знаете, какой тип команды при использовании, параметр **CommandType** свойство предписывает ADO, чтобы перейти непосредственно к соответствующему коду. Если **CommandType** свойства не соответствует типу команды в **CommandText** свойство, произошла ошибка при вызове [Execute](../../../ado/reference/ado-api/execute-method-ado-command.md) метод.  
  
## <a name="applies-to"></a>Объект применения  
 [Объект Command (ADO)](../../../ado/reference/ado-api/command-object-ado.md)  
  
## <a name="see-also"></a>См. также  
 [ActiveConnection, CommandText, CommandTimeout, CommandType, размер и направление свойства пример (Visual Basic)](../../../ado/reference/ado-api/activeconnection-commandtext-commandtimeout-commandtype-size-example-vb.md)   
 [ActiveConnection, CommandText, CommandTimeout, CommandType, размер и направление пример свойства (Visual C++)](../../../ado/reference/ado-api/activeconnection-commandtext-commandtimeout-commandtype-size-example-vc.md)   
 [ActiveConnection, CommandText, CommandTimeout, CommandType, размер и направление примеры свойств (JScript)](../../../ado/reference/ado-api/activeconnection-commandtext-timeout-type-size-example-jscript.md)
