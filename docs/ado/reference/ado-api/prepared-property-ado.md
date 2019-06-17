---
title: Подготовленный свойство (ADO) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Command15::Prepared
helpviewer_keywords:
- Prepared property [ADO]
ms.assetid: 11ca8825-765e-4bb4-a6ce-3f6564ad8755
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: c762de42fd12509a56fcc22584b4afa57be2eaa5
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "66703141"
---
# <a name="prepared-property-ado"></a>Свойство Prepared (ADO)
Указывает, следует ли сохранить скомпилированную версию [команда](../../../ado/reference/ado-api/command-object-ado.md) перед выполнением.  
  
## <a name="settings-and-return-values"></a>Параметры и возвращаемые значения  
 Возвращает или задает **логическое** значение, которое, если значение **True**, указывает, что команду следует подготовить.  
  
## <a name="remarks"></a>Примечания  
 Используйте **подготовленных** свойства для поставщика данных сохранить подготовленную (или скомпилированную) версию запрос, указанный в [CommandText](../../../ado/reference/ado-api/commandtext-property-ado.md) свойства перед [команда](../../../ado/reference/ado-api/command-object-ado.md) объекта Первое выполнение. Это может замедлить выполнение первой команды, но как только поставщик компилирует команду, поставщик будет использовать скомпилированную версию команды для любого последующего выполнения, что приведет к повышению производительности.  
  
 Если свойство **False**, поставщик будет выполнять **команда** объекта непосредственно, без создания скомпилированная версия.  
  
 Если поставщик не поддерживает команды подготовки, ее могут возвращать ошибку, если это свойство имеет значение **True**. Если поставщик не возвращает ошибку, просто игнорирует запрос на подготовку команды и наборы **подготовленных** свойства **False**.  
  
## <a name="applies-to"></a>Объект применения  
 [Объект Command (ADO)](../../../ado/reference/ado-api/command-object-ado.md)  
  
## <a name="see-also"></a>См. также  
 [Пример свойства Prepared (Visual Basic)](../../../ado/reference/ado-api/prepared-property-example-vb.md)   
 [Пример свойства Prepared (Visual C++)](../../../ado/reference/ado-api/prepared-property-example-vc.md)   
