---
title: Свойство IsolationLevel | Документы Microsoft
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Connection15::IsolationLevel
helpviewer_keywords:
- IsolationLevel property
ms.assetid: ea84e4b2-fbf2-4eef-b9ce-796b22e21800
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 326f145da9c2e80b7f4765a0c4bae1a657f4ee25
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="isolationlevel-property"></a>Свойство IsolationLevel
Указывает уровень изоляции для [подключения](../../../ado/reference/ado-api/connection-object-ado.md) объекта.  
  
## <a name="settings-and-return-values"></a>Параметры и возвращаемые значения  
 Возвращает или задает [IsolationLevelEnum](../../../ado/reference/ado-api/isolationlevelenum.md) значение. Значение по умолчанию — **adXactReadCommitted**.  
  
## <a name="remarks"></a>Замечания  
 Используйте **IsolationLevel** свойство, чтобы задать уровень изоляции **подключения** объекта. Параметр вступает в силу только при следующем вызове [BeginTrans](../../../ado/reference/ado-api/begintrans-committrans-and-rollbacktrans-methods-ado.md) метод. Если уровень изоляции, запрашивается недоступен, поставщик может возвращать больше следующий уровень изоляции без обновления **IsolationLevel** свойство.  
  
 **IsolationLevel** свойство доступно для чтения/записи.  
  
> [!NOTE]
>  **Удаленное использование службы данных** при использовании на стороне клиента **подключения** объекта, **IsolationLevel** может быть задано только в **adXactUnspecified**. Так как пользователи работают с отключенной **записей** объектов на стороне клиента кэша, может быть многопользовательской проблемы. Для экземпляра попытку обновления той же записи двух различных пользователей удаленной службы данных просто позволяет пользователю, выполняющему сначала обновляет запись для «win». Запрос на обновление второго пользователя будут завершаться ошибкой.  
  
## <a name="applies-to"></a>Объект применения  
 [Объект Connection (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)  
  
## <a name="see-also"></a>См. также  
 [IsolationLevel и пример свойства режима (Visual Basic)](../../../ado/reference/ado-api/isolationlevel-and-mode-properties-example-vb.md)   
 [IsolationLevel и пример свойства режима (VC ++)](../../../ado/reference/ado-api/isolationlevel-and-mode-properties-example-vc.md)   
