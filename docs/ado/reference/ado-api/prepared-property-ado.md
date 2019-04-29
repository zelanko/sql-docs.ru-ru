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
manager: craigg
ms.openlocfilehash: d7317b6b9a5251c8d104e6c2153ec8c009b2aea7
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63027807"
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
