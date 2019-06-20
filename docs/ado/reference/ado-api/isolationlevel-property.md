---
title: Свойство IsolationLevel | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Connection15::IsolationLevel
helpviewer_keywords:
- IsolationLevel property
ms.assetid: ea84e4b2-fbf2-4eef-b9ce-796b22e21800
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 9e027e325ec27bf5a80cf4df85afcfe59656ce3c
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "66697586"
---
# <a name="isolationlevel-property"></a>Свойство IsolationLevel
Указывает уровень изоляции для [подключения](../../../ado/reference/ado-api/connection-object-ado.md) объекта.  
  
## <a name="settings-and-return-values"></a>Параметры и возвращаемые значения  
 Возвращает или задает [IsolationLevelEnum](../../../ado/reference/ado-api/isolationlevelenum.md) значение. По умолчанию используется **adXactReadCommitted**.  
  
## <a name="remarks"></a>Примечания  
 Используйте **IsolationLevel** свойство для задания уровня изоляции **подключения** объекта. Этот параметр не вступили в силу только при следующем вызове [BeginTrans](../../../ado/reference/ado-api/begintrans-committrans-and-rollbacktrans-methods-ado.md) метод. Если уровень изоляции, запрашивается недоступен, это означает, поставщик может вернуть больше уровня изоляции без обновления **IsolationLevel** свойство.  
  
 **IsolationLevel** свойство доступно для чтения/записи.  
  
> [!NOTE]
>  **Удаленное использование службы данных** при использовании на стороне клиента **подключения** объекта, **IsolationLevel** свойству можно присвоить только значение **adXactUnspecified**. Так как пользователи работают с отключенной **записей** объекты на стороне клиента кэша, могут возникнуть проблемы в многопользовательской. К примеру попытку обновления той же записи два разных пользователя удаленной службы данных просто позволяет пользователю, выполняющему сначала обновляет запись для «win». Запрос на обновление второго пользователя будут завершаться ошибкой.  
  
## <a name="applies-to"></a>Объект применения  
 [Объект Connection (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)  
  
## <a name="see-also"></a>См. также  
 [Примеры IsolationLevel и Mode свойства (Visual Basic)](../../../ado/reference/ado-api/isolationlevel-and-mode-properties-example-vb.md)   
 [Примеры IsolationLevel и Mode свойства (Visual C++)](../../../ado/reference/ado-api/isolationlevel-and-mode-properties-example-vc.md)   
