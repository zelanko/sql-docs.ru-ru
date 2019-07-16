---
title: Запрос свойства (динамическое) (ADO) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- Prompt property [ADO]
ms.assetid: c4f001b5-8d16-4d39-a42e-c0e2faaaceaf
author: MightyPen
ms.author: genemi
ms.openlocfilehash: cde7a5ad0324bc7d5cde5e1a794eeb9e2cb3381a
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67931582"
---
# <a name="prompt-property-dynamic-ado"></a>Свойство Prompt (динамическое) (ADO)
Указывает, должен ли поставщик OLE DB запрашивать пользователя сведения об инициализации.  
  
## <a name="settings-and-return-values"></a>Параметры и возвращаемые значения  
 Задает и возвращает [ConnectPromptEnum](../../../ado/reference/ado-api/connectpromptenum.md) значение.  
  
## <a name="remarks"></a>Примечания  
 **Prompt** является динамической, что могут добавляться в [подключения](../../../ado/reference/ado-api/connection-object-ado.md) объекта [свойства](../../../ado/reference/ado-api/properties-collection-ado.md) коллекции с помощью поставщика OLE DB. Запрашивать сведения об инициализации, поставщики OLE DB обычно будет отображать диалоговое окно для пользователя.  
  
 Динамические свойства [подключения](../../../ado/reference/ado-api/connection-object-ado.md) объекта были утеряны при **подключения** закрыт. **Prompt** необходимо сбросить свойство до повторного открытия **подключения** использовать значение, отличное от по умолчанию.  
  
> [!NOTE]
>  Не следует указывать, что поставщик должен запросить пользователя в сценариях, в которых пользователь не сможет ответить на диалоговое окно. Например пользователь не будет отвечать, если приложение выполняется в серверной системе, а не на клиенте пользователя или приложения, выполнив в системе нет пользователя, выполнившего вход. В этом случае приложение будет бесконечно ожидать ответа и зависать.  
  
## <a name="usage"></a>Использование  
  
```  
Set cn = New Connection  
cn.Provider = "SQLOLEDB"  
cn.Properties("Prompt") = adPromptNever    ' do not prompt the user  
```  
  
## <a name="applies-to"></a>Объект применения  
 [Объект Connection (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)
