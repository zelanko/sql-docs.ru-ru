---
description: Свойство ParentURL (ADO)
title: Свойство Парентурл (ADO) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
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
author: rothja
ms.author: jroth
ms.openlocfilehash: e3a8323223f97034750c7e6bf7927ac87aefd3bd
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2020
ms.locfileid: "88990115"
---
# <a name="parenturl-property-ado"></a>Свойство ParentURL (ADO)
Указывает абсолютную строку URL-адреса, указывающую на родительскую [запись](./record-object-ado.md) текущего объекта **Record** .  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает **строковое** значение, указывающее URL-адрес родительской **записи**.  
  
## <a name="remarks"></a>Remarks  
 Свойство **парентурл** зависит от источника, используемого для открытия объекта **Record** . Например, **запись** может быть открыта с источником, содержащим относительный путь к каталогу, на который ссылается свойство [ActiveConnection](./activeconnection-property-ado.md) .  
  
 Предположим, "вторая" — это папка, которая находится в разделе "First". Откройте объект **Record** , используя следующий синтаксис:  
  
```  
record.ActiveConnection = "https://first"  
record.Open "second"  
```  
  
 Теперь значение `the` свойства **парентурл** равно `"https://first"` , то же, что и **ActiveConnection**.  
  
 Источник также может быть абсолютным URL-адресом, таким как, `"https://first/second"` . Затем свойство **парентурл** — `"https://first"` уровень выше `"second"` .  
  
 Это свойство может иметь значение null, если:  
  
-   Родительский объект для текущего объекта отсутствует; Например, если объект **Record** представляет корень каталога.  
  
-   Объект **Record** представляет сущность, которая не может быть указана с помощью URL-адреса.  
  
 Это свойство доступно только для чтения.  
  
> [!NOTE]
>  Это свойство поддерживается только поставщиками источников документов, такими как [поставщик OLE DB Майкрософт для публикации в Интернете](../../guide/appendixes/microsoft-ole-db-provider-for-internet-publishing.md). Дополнительные сведения см. в разделе [записи и предоставляемые поставщиком поля](../../guide/data/records-and-provider-supplied-fields.md).  
  
> [!NOTE]
>  URL-адреса, использующие схему HTTP, автоматически вызывают [поставщик OLE DB Майкрософт для публикации в Интернете](../../guide/appendixes/microsoft-ole-db-provider-for-internet-publishing.md). Дополнительные сведения см. в разделе [абсолютные и относительные URL-адреса](../../guide/data/absolute-and-relative-urls.md).  
  
> [!NOTE]
>  Если текущая запись содержит запись данных из **набора записей**ADO, то доступ к свойству **парентурл** вызывает ошибку времени выполнения, что означает, что URL-адрес невозможен.  
  
## <a name="applies-to"></a>Применение  
 [Объект Record (ADO)](./record-object-ado.md)