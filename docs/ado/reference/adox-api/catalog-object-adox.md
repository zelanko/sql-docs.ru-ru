---
description: Объект Catalog (ADOX)
title: Объект каталога (ADOX) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
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
ms.openlocfilehash: 8329c4a94a6c9e01f0730b3244eabc6c74511cfa
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2020
ms.locfileid: "88985315"
---
# <a name="catalog-object-adox"></a>Объект Catalog (ADOX)
Содержит коллекции ([таблицы](./tables-collection-adox.md), [представления](./views-collection-adox.md), [пользователей](./users-collection-adox.md), [группы](./groups-collection-adox.md)и [процедуры](./procedures-collection-adox.md)), которые описывают Каталог схемы источника данных.  
  
## <a name="remarks"></a>Remarks  
 Объект **каталога** можно изменить, добавив или удалив объекты или изменив существующие объекты. Некоторые поставщики могут не поддерживать все объекты **каталога** или могут поддерживать только просмотр сведений о схеме.  
  
 Свойства и методы объекта **каталога** позволяют:  
  
-   Откройте каталог, задав для свойства [ActiveConnection](./activeconnection-property-adox.md) объект [соединения](../ado-api/connection-object-ado.md) ADO или допустимую строку подключения.  
  
-   Создайте новый каталог с помощью метода [CREATE](./create-method-adox.md) .  
  
-   Определите владельцев объектов в **каталоге** с помощью методов [примеры методов getobjectowner](./getobjectowner-method-adox.md) и [SetObjectOwner](./setobjectowner-method.md) .  
  
 Этот раздел содержит следующий раздел.  
  
-   [Свойства, методы и события объекта Catalog](./catalog-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>См. также  
 [Пример свойства ActiveConnection каталога (Visual Basic)](./catalog-activeconnection-property-example-vb.md)   
 [Пример свойств Command и CommandText (Visual Basic)](./command-and-commandtext-properties-example-vb.md)   
 [Пример метода Close соединения, свойство типа таблицы (Visual Basic)](./connection-close-method-table-type-property-example-vb.md)   
 [Пример метода Create (Visual Basic)](./create-method-example-vb.md)   
 [Пример свойств для добавления ключей, типа ключа, RelatedColumn, RelatedTable и UpdateRule (Visual Basic)](./keys-append-method-key-type-relatedcolumn-relatedtable-example-vb.md)   
 [Коллекция Parameters, пример свойства Command (Visual Basic)](./parameters-collection-command-property-example-vb.md)   
 [Пример свойства ParentCatalog (Visual Basic)](./parentcatalog-property-example-vb.md)   
 [Пример метода Append для процедур (Visual Basic)](./procedures-append-method-example-vb.md)   
 [Пример метода Delete процедур (Visual Basic)](./procedures-delete-method-example-vb.md)   
 [Пример метода обновления процедур (Visual Basic)](./procedures-refresh-method-example-vb.md)   
 [Пример представлений и коллекций полей (Visual Basic)](./views-and-fields-collections-example-vb.md)   
 [Пример метода Append для представлений (Visual Basic)](./views-append-method-example-vb.md)   
 [Пример коллекции Views, свойство CommandText (Visual Basic)](./views-collection-commandtext-property-example-vb.md)   
 [Пример метода Delete представлений (Visual Basic)](./views-delete-method-example-vb.md)   
 [Пример метода Refresh для представлений (Visual Basic)](./views-refresh-method-example-vb.md)   
 [Коллекция Groups (ADOX)](./groups-collection-adox.md)   
 [Коллекция процедур (ADOX)](./procedures-collection-adox.md)   
 [Коллекция Tables (ADOX)](./tables-collection-adox.md)   
 [Коллекция пользователей (ADOX)](./users-collection-adox.md)   
 [Коллекция Views (ADOX)](./views-collection-adox.md)