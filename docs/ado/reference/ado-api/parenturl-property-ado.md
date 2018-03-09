---
title: "Свойство ParentURL (ADO) | Документы Microsoft"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- _Record::ParentURL
helpviewer_keywords:
- ParentURL property [ADO]
ms.assetid: 65120ce6-3900-4cd4-b322-3b9816d74737
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: eca04999eece256ef22503c4d227ffcec297c79a
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/09/2018
---
# <a name="parenturl-property-ado"></a>Свойство ParentURL (ADO)
Указывает строку абсолютный URL-адрес, указывающий на родительский [запись](../../../ado/reference/ado-api/record-object-ado.md) текущего **записи** объекта.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает **строка** значение, указывающее URL-адрес родительского **записи**.  
  
## <a name="remarks"></a>Remarks  
 **ParentURL** свойство зависит от источника, используемую для открытия **записи** объекта. Например **запись** могут быть открыты в источник, содержащий относительный путь к каталогу, который ссылается [ActiveConnection](../../../ado/reference/ado-api/activeconnection-property-ado.md) свойство.  
  
 Предположим, что «second» папке содержится в разделе «первый». Откройте **записи** объекта, используя следующий синтаксис:  
  
```  
record.ActiveConnection = "http://first"  
record.Open "second"  
```  
  
 Теперь значение `the` **ParentURL** свойство `"http://first"`, то же, что **ActiveConnection**.  
  
 Источник может также быть абсолютный URL-адрес такие как `"http://first/second"`. **ParentURL** свойство будет `"http://first"`, уровнем выше `"second"`.  
  
 Это свойство может иметь значение null, если:  
  
-   Родительский объект отсутствует текущий объект; Например если **запись** представляет корневой каталог.  
  
-   **Запись** представляет сущность, которая не может указываться с URL-адреса.  
  
 Это свойство предназначено только для чтения.  
  
> [!NOTE]
>  Это свойство поддерживается только поставщиками исходного документа, такие как [поставщик Microsoft OLE DB для публикаций в Интернете](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-internet-publishing.md). Дополнительные сведения см. в разделе [записи и поля Provider-Supplied](../../../ado/guide/data/records-and-provider-supplied-fields.md).  
  
> [!NOTE]
>  URL-адреса, с помощью схемы http автоматически вызывает [поставщик Microsoft OLE DB для публикаций в Интернете](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-internet-publishing.md). Дополнительные сведения см. в разделе [абсолютные и относительные URL-адреса](../../../ado/guide/data/absolute-and-relative-urls.md).  
  
> [!NOTE]
>  Если текущая запись содержит запись данных из ADO **записей**, доступ к свойству **ParentURL** свойство вызывает ошибку времени выполнения, указывает, что URL-адрес не возможно.  
  
## <a name="applies-to"></a>Объект применения  
 [Объект Record (ADO)](../../../ado/reference/ado-api/record-object-ado.md)
