---
title: Свойство Prompt — Dynamic (ADO) | Документация Майкрософт
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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "67931582"
---
# <a name="prompt-property-dynamic-ado"></a>Свойство Prompt (динамическое) (ADO)
Указывает, должен ли поставщик OLE DB запрашивать сведения об инициализации у пользователя.  
  
## <a name="settings-and-return-values"></a>Параметры и возвращаемые значения  
 Задает и возвращает значение [коннектпромптенум](../../../ado/reference/ado-api/connectpromptenum.md) .  
  
## <a name="remarks"></a>Remarks  
 **Prompt** — это динамическое свойство, которое может быть добавлено к коллекции [свойств](../../../ado/reference/ado-api/properties-collection-ado.md) объекта [Connection](../../../ado/reference/ado-api/connection-object-ado.md) поставщиком OLE DB. Для запроса сведений об инициализации поставщик OLE DB обычно отображает диалоговое окно для пользователя.  
  
 При закрытии **соединения** динамические свойства объекта [соединения](../../../ado/reference/ado-api/connection-object-ado.md) теряются. Необходимо сбросить свойство **Prompt** , прежде чем повторно открыть **соединение** , чтобы использовать значение, отличное от значения по умолчанию.  
  
> [!NOTE]
>  Не указывайте, что поставщик должен запрашивать пользователя в сценариях, в которых пользователь не сможет ответить на это диалоговое окно. Например, пользователь не сможет ответить, если приложение выполняется в серверной системе, а не на клиенте пользователя, или если приложение выполняется в системе без входа пользователя в систему. В таких случаях приложение будет ожидать ответа в течение неограниченного времени и кажется заблокированным.  
  
## <a name="usage"></a>Использование  
  
```  
Set cn = New Connection  
cn.Provider = "SQLOLEDB"  
cn.Properties("Prompt") = adPromptNever    ' do not prompt the user  
```  
  
## <a name="applies-to"></a>Применяется к  
 [Объект Connection (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)
