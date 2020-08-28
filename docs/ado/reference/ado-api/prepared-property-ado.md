---
description: Свойство Prepared (ADO)
title: Подготовленное свойство (ADO) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 7352d21467061a38bd7e2443ecb52fdb59bd7696
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2020
ms.locfileid: "88990045"
---
# <a name="prepared-property-ado"></a>Свойство Prepared (ADO)
Указывает, следует ли сохранять скомпилированную версию [команды](./command-object-ado.md) перед выполнением.  
  
## <a name="settings-and-return-values"></a>Параметры и возвращаемые значения  
 Задает или возвращает **логическое** значение, которое, если задано значение **true**, указывает, что команда должна быть подготовлена.  
  
## <a name="remarks"></a>Remarks  
 Используйте **подготовленное** свойство, чтобы поставщик сохранял подготовленную (или скомпилированную) версию запроса, заданную в свойстве [CommandText](./commandtext-property-ado.md) перед первым выполнением объекта [команды](./command-object-ado.md) . Это может замедлять первое выполнение команды, но после того, как поставщик компилирует команду, поставщик будет использовать скомпилированную версию команды для всех последующих выполнений, что приведет к повышению производительности.  
  
 Если свойство имеет **значение false**, поставщик будет выполнять **Командный** объект напрямую без создания скомпилированной версии.  
  
 Если поставщик не поддерживает подготовку команд, он может вернуть ошибку, если это свойство имеет значение **true**. Если поставщик не возвращает ошибку, он просто игнорирует запрос на подготовку команды и устанавливает для свойства **Prepared** значение **false**.  
  
## <a name="applies-to"></a>Применение  
 [Объект Command (ADO)](./command-object-ado.md)  
  
## <a name="see-also"></a>См. также  
 [Пример подготовленного свойства (Visual Basic)](./prepared-property-example-vb.md)   
 [Пример свойства Prepared (Visual C++)](./prepared-property-example-vc.md)