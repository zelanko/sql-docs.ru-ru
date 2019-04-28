---
title: Пример свойства ParentCatalog (ADOX) | Документация Майкрософт
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 10d6715a19212c87ece9c890ee99516571713d4f
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62710333"
---
# <a name="parentcatalog-property-adox"></a>Свойство ParentCatalog (ADOX)
Указывает каталог родительского объекта таблицы, пользователя или столбец для предоставления доступа к свойствам конкретного поставщика.  
  
## <a name="settings-and-return-values"></a>Параметры и возвращаемые значения  
 Задает и возвращает [каталога](../../../ado/reference/adox-api/catalog-object-adox.md) объекта. Установка **ParentCatalog** открытому **каталога** разрешает доступ к свойствам поставщика перед добавлением таблицы или столбца для **каталога** коллекции.  
  
## <a name="remarks"></a>Примечания  
 Некоторые поставщики данных позволяет значениям свойств от поставщика, должны быть записаны только во время создания: то есть когда таблица или столбец добавляется к его **каталога** коллекции. Для доступа к этим свойствам перед добавлением этих объектов для **каталога**, укажите **каталога** в **ParentCatalog** свойства первого.  
  
 Произошла ошибка, если таблица или столбец добавляется к другой **каталога** чем **ParentCatalog**.  
  
## <a name="applies-to"></a>Объект применения  
  
|||  
|-|-|  
|[Объект Column (ADOX)](../../../ado/reference/adox-api/column-object-adox.md)|[Объект Table (ADOX)](../../../ado/reference/adox-api/table-object-adox.md)|  
|[Объект User (ADOX)](../../../ado/reference/adox-api/user-object-adox.md)||  
  
## <a name="see-also"></a>См. также  
 [Пример свойства ParentCatalog (Visual Basic)](../../../ado/reference/adox-api/parentcatalog-property-example-vb.md)
