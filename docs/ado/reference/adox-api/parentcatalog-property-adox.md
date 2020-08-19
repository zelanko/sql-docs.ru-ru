---
description: Свойство ParentCatalog (ADOX)
title: Свойство ParentCatalog (ADOX) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _User::get_ParentCatalog
- _Column::ParentCatalog
- _Table::put_ParentCatalog
- _Group::put_ParentCatalog
- _Column::get_ParentCatalog
- _Table::PutParentCatalog
- _Group::putref_ParentCatalog
- _Group::ParentCatalog
- _Column::PutParentCatalog
- _Column::put_ParentCatalog
- _Group::get_ParentCatalog
- _User::put_ParentCatalog
- _User::putref_ParentCatalog
- _Table::get_ParentCatalog
- _Group::PutParentCatalog
- _Table::ParentCatalog
- _Column::GetParentCatalog
- _Table::PutRefParentCatalog
- _User::GetParentCatalog
- _Table::GetParentCatalog
- _Table::putref_ParentCatalog
- _User::PutParentCatalog
- _User::ParentCatalog
- _User::PutRefParentCatalog
- _Group::GetParentCatalog
- _Group::PutRefParentCatalog
helpviewer_keywords:
- ParentCatalog property [ADOX]
ms.assetid: a0bb2ed8-d4cb-4f92-8de7-769bbe0e6273
author: rothja
ms.author: jroth
ms.openlocfilehash: 93d15cdac3d8f7a47c74a783d176d806271f68a3
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88439726"
---
# <a name="parentcatalog-property-adox"></a>Свойство ParentCatalog (ADOX)
Указывает родительский каталог объекта таблицы, пользователя или столбца, который предоставляет доступ к свойствам, зависящим от поставщика.  
  
## <a name="settings-and-return-values"></a>Параметры и возвращаемые значения  
 Задает и возвращает объект [каталога](../../../ado/reference/adox-api/catalog-object-adox.md) . Установка **ParentCatalog** в открытый **Каталог** предоставляет доступ к свойствам, зависящим от поставщика, до добавления таблицы или столбца в коллекцию **каталогов** .  
  
## <a name="remarks"></a>Remarks  
 Некоторые поставщики данных позволяют записывать значения свойств, определяемые поставщиком, только при их создании: то есть когда таблица или столбец добавляются в коллекцию **каталогов** . Чтобы получить доступ к этим свойствам перед добавлением этих объектов в **Каталог**, сначала укажите **Каталог** в свойстве **ParentCatalog** .  
  
 Ошибка возникает при добавлении таблицы или столбца к **каталогу** , отличному от каталога **ParentCatalog**.  
  
## <a name="applies-to"></a>Применение  

:::row:::
    :::column:::
        [Объект Column (ADOX)](../../../ado/reference/adox-api/column-object-adox.md)  
    :::column-end:::
    :::column:::
        [Объект Table (ADOX)](../../../ado/reference/adox-api/table-object-adox.md)  
    :::column-end:::
    :::column:::
        [Объект User (ADOX)](../../../ado/reference/adox-api/user-object-adox.md)  
    :::column-end:::
:::row-end:::

## <a name="see-also"></a>См. также:  
 [Пример свойства ParentCatalog (Visual Basic)](../../../ado/reference/adox-api/parentcatalog-property-example-vb.md)
