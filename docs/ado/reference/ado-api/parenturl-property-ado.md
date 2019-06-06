---
title: Свойство ParentURL (ADO) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Record::ParentURL
helpviewer_keywords:
- ParentURL property [ADO]
ms.assetid: 65120ce6-3900-4cd4-b322-3b9816d74737
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 65704cea2a396e0f03de4bbcdc9f031f4c9af583
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/05/2019
ms.locfileid: "66703467"
---
# <a name="parenturl-property-ado"></a>Свойство ParentURL (ADO)
Указывает строку абсолютный URL-адрес, указывающий родительский [записи](../../../ado/reference/ado-api/record-object-ado.md) текущего **записи** объекта.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает **строка** значение, указывающее URL-адрес родительского **записи**.  
  
## <a name="remarks"></a>Примечания  
 **ParentURL** свойство зависит от источника, используемый для открытия **записи** объекта. Например **записи** могут быть открыты в источник, содержащий относительный путь к каталогу, который ссылается [ActiveConnection](../../../ado/reference/ado-api/activeconnection-property-ado.md) свойство.  
  
 Предположим, что «во-вторых» папка содержится в разделе «первый». Откройте **записи** , используя следующий синтаксис:  
  
```  
record.ActiveConnection = "https://first"  
record.Open "second"  
```  
  
 Теперь значение `the` **ParentURL** свойство `"https://first"`, совпадение с кодом **ActiveConnection**.  
  
 Источник может также быть абсолютный URL-адрес такие как `"https://first/second"`. **ParentURL** свойство будет `"https://first"`, уровнем выше `"second"`.  
  
 Это свойство может иметь значение null, если:  
  
-   Родительский элемент отсутствует текущий объект; Например если **запись** представляет корневой каталог.  
  
-   **Запись** представляет сущность, которая не может указываться с URL-адрес.  
  
 Это свойство доступно только для чтения.  
  
> [!NOTE]
>  Это свойство поддерживается только поставщиками исходного документа, такие как [поставщик Microsoft OLE DB для публикаций в Интернете](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-internet-publishing.md). Дополнительные сведения см. в разделе [записи и поля Provider-Supplied](../../../ado/guide/data/records-and-provider-supplied-fields.md).  
  
> [!NOTE]
>  URL-адреса, с использованием схемы http, автоматически вызывает метод [поставщик Microsoft OLE DB для публикаций в Интернете](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-internet-publishing.md). Дополнительные сведения см. в разделе [абсолютные и относительные URL-адреса](../../../ado/guide/data/absolute-and-relative-urls.md).  
  
> [!NOTE]
>  Если текущая запись содержит запись данных из ADO **записей**, доступ к свойству **ParentURL** свойство вызывает ошибку времени выполнения, указывает, что URL-адрес не возможно.  
  
## <a name="applies-to"></a>Объект применения  
 [Объект Record (ADO)](../../../ado/reference/ado-api/record-object-ado.md)
