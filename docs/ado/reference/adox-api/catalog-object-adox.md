---
description: Объект Catalog (ADOX)
title: Объект каталога (ADOX) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Catalog
helpviewer_keywords:
- Catalog object [ADOX]
ms.assetid: bb651639-a488-4e38-b6de-0ed99fa4dd92
author: rothja
ms.author: jroth
ms.openlocfilehash: 35fa08ba0d93a7adacf6d58338f4808e2a5eba9e
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88440386"
---
# <a name="catalog-object-adox"></a>Объект Catalog (ADOX)
Содержит коллекции ([таблицы](../../../ado/reference/adox-api/tables-collection-adox.md), [представления](../../../ado/reference/adox-api/views-collection-adox.md), [пользователей](../../../ado/reference/adox-api/users-collection-adox.md), [группы](../../../ado/reference/adox-api/groups-collection-adox.md)и [процедуры](../../../ado/reference/adox-api/procedures-collection-adox.md)), которые описывают Каталог схемы источника данных.  
  
## <a name="remarks"></a>Remarks  
 Объект **каталога** можно изменить, добавив или удалив объекты или изменив существующие объекты. Некоторые поставщики могут не поддерживать все объекты **каталога** или могут поддерживать только просмотр сведений о схеме.  
  
 Свойства и методы объекта **каталога** позволяют:  
  
-   Откройте каталог, задав для свойства [ActiveConnection](../../../ado/reference/adox-api/activeconnection-property-adox.md) объект [соединения](../../../ado/reference/ado-api/connection-object-ado.md) ADO или допустимую строку подключения.  
  
-   Создайте новый каталог с помощью метода [CREATE](../../../ado/reference/adox-api/create-method-adox.md) .  
  
-   Определите владельцев объектов в **каталоге** с помощью методов [примеры методов getobjectowner](../../../ado/reference/adox-api/getobjectowner-method-adox.md) и [SetObjectOwner](../../../ado/reference/adox-api/setobjectowner-method.md) .  
  
 Этот раздел содержит следующий раздел.  
  
-   [Свойства, методы и события объекта Catalog](../../../ado/reference/adox-api/catalog-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>См. также:  
 [Пример свойства ActiveConnection каталога (Visual Basic)](../../../ado/reference/adox-api/catalog-activeconnection-property-example-vb.md)   
 [Пример свойств Command и CommandText (Visual Basic)](../../../ado/reference/adox-api/command-and-commandtext-properties-example-vb.md)   
 [Пример метода Close соединения, свойство типа таблицы (Visual Basic)](../../../ado/reference/adox-api/connection-close-method-table-type-property-example-vb.md)   
 [Пример метода Create (Visual Basic)](../../../ado/reference/adox-api/create-method-example-vb.md)   
 [Пример свойств для добавления ключей, типа ключа, RelatedColumn, RelatedTable и UpdateRule (Visual Basic)](../../../ado/reference/adox-api/keys-append-method-key-type-relatedcolumn-relatedtable-example-vb.md)   
 [Коллекция Parameters, пример свойства Command (Visual Basic)](../../../ado/reference/adox-api/parameters-collection-command-property-example-vb.md)   
 [Пример свойства ParentCatalog (Visual Basic)](../../../ado/reference/adox-api/parentcatalog-property-example-vb.md)   
 [Пример метода Append для процедур (Visual Basic)](../../../ado/reference/adox-api/procedures-append-method-example-vb.md)   
 [Пример метода Delete процедур (Visual Basic)](../../../ado/reference/adox-api/procedures-delete-method-example-vb.md)   
 [Пример метода обновления процедур (Visual Basic)](../../../ado/reference/adox-api/procedures-refresh-method-example-vb.md)   
 [Пример представлений и коллекций полей (Visual Basic)](../../../ado/reference/adox-api/views-and-fields-collections-example-vb.md)   
 [Пример метода Append для представлений (Visual Basic)](../../../ado/reference/adox-api/views-append-method-example-vb.md)   
 [Пример коллекции Views, свойство CommandText (Visual Basic)](../../../ado/reference/adox-api/views-collection-commandtext-property-example-vb.md)   
 [Пример метода Delete представлений (Visual Basic)](../../../ado/reference/adox-api/views-delete-method-example-vb.md)   
 [Пример метода Refresh для представлений (Visual Basic)](../../../ado/reference/adox-api/views-refresh-method-example-vb.md)   
 [Коллекция Groups (ADOX)](../../../ado/reference/adox-api/groups-collection-adox.md)   
 [Коллекция процедур (ADOX)](../../../ado/reference/adox-api/procedures-collection-adox.md)   
 [Коллекция Tables (ADOX)](../../../ado/reference/adox-api/tables-collection-adox.md)   
 [Коллекция пользователей (ADOX)](../../../ado/reference/adox-api/users-collection-adox.md)   
 [Коллекция Views (ADOX)](../../../ado/reference/adox-api/views-collection-adox.md)
