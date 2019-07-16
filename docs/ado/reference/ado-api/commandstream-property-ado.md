---
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 23ec65380bfea16d38f02cab0a070ab69f85d525
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67919748"
---
# <a name="commandstream-property-ado"></a>Свойство CommandStream (ADO)
Указывает поток, используемый в качестве входных данных для [команда](../../../ado/reference/ado-api/command-object-ado.md) объекта.  
  
## <a name="settings-and-return-values"></a>Параметры и возвращаемые значения  
 Задает или возвращает поток, используемый в качестве входных данных для **команда** объекта. Формат для этого потока от поставщика; см. сведения о документации вашего поставщика. Это свойство похоже на [CommandText](../../../ado/reference/ado-api/commandtext-property-ado.md) свойство, которое используется для указания строка ввода **команда**.  
  
## <a name="remarks"></a>Примечания  
 **CommandStream** и **CommandText** взаимно исключают друг друга. Когда пользователь задает **CommandStream** свойство, **CommandText** свойство устанавливается в пустую строку (»»). Если пользователь задает **CommandText** свойство, **CommandStream** свойству будет присвоено **ничего не**.  
  
 Поведение **Command.Parameters.Refresh** и **Command.Prepare** методы определяются поставщиком. Значения параметров в потоке не могут быть обновлены.  
  
 Входной поток недоступен для других объектов ADO, которые возвращают источник **команда**. Например если [источника](../../../ado/reference/ado-api/source-property-ado-recordset.md) из [набор записей](../../../ado/reference/ado-api/recordset-object-ado.md) присваивается **команда** объект, имеющий поток в качестве входных данных, **Recordset.Source** продолжает возвращать **CommandText** свойство, которое содержит пустую строку ("»), а не содержимое потока **CommandStream** свойство.  
  
 При использовании поток команды (как указано **CommandStream**), единственным допустимым [CommandTypeEnum](../../../ado/reference/ado-api/commandtypeenum.md) значений в параметре [CommandType](../../../ado/reference/ado-api/commandtype-property-ado.md) свойства  **adCmdText** и **adCmdUnknown**. Любое другое значение приводит к ошибке.  
  
## <a name="applies-to"></a>Объект применения  
 [Объект Command (ADO)](../../../ado/reference/ado-api/command-object-ado.md)  
  
## <a name="see-also"></a>См. также  
 [Свойство CommandText (ADO)](../../../ado/reference/ado-api/commandtext-property-ado.md)   
 [Свойство Dialect](../../../ado/reference/ado-api/dialect-property.md)   
 [CommandTypeEnum](../../../ado/reference/ado-api/commandtypeenum.md)
