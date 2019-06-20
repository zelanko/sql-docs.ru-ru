---
title: Append-метод (коллекция Views ADOX) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Views::raw_Append
- Views::Append
helpviewer_keywords:
- Append method [ADOX]
ms.assetid: 6070fd58-3237-4c77-a966-5b39ce5d57e4
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: f5f58ff2f38ff80d90750901b8943efc00f389c6
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "66718952"
---
# <a name="append-method-adox-views"></a>Метод Append (коллекция Views ADOX)
Создает новый [представление](../../../ado/reference/adox-api/view-object-adox.md) объект и добавляет его к [представления](../../../ado/reference/adox-api/views-collection-adox.md) коллекции.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Views.Append Name, Command  
```  
  
#### <a name="parameters"></a>Параметры  
 *Name*  
 Объект **строка** значение, указывающее имя представления для создания.  
  
 *Command*  
 ADO [команда](../../../ado/reference/ado-api/command-object-ado.md) , представляющий представление, чтобы создать.  
  
## <a name="remarks"></a>Примечания  
 Создает новое представление источника данных с именем и атрибутами, заданными в **команда** объекта.  
  
 Если текст команды, который указывает пользователь представляет процедуру, а не представление, поведение зависит от поставщика. **Добавление** завершится ошибкой, если поставщик не поддерживает сохранение команды.  
  
> [!NOTE]
>  При использовании поставщика OLE DB для Jet (Майкрософт), **представления** коллекции **Append** метод позволит вам указать **процедуры** вместо **представление**  в *команда* параметра. **Процедуры** будут добавляться к источнику данных и добавляется **представления** коллекции. После **Append**, если **процедуры** и **представления** обновляются коллекций, **процедуры** больше не будет в **Представления** коллекции и будет отображаться в **процедуры** коллекции.  
  
## <a name="applies-to"></a>Объект применения  
 [Коллекция Views (ADOX)](../../../ado/reference/adox-api/views-collection-adox.md)  
  
## <a name="see-also"></a>См. также  
 [Представления метода пример Append (Visual Basic)](../../../ado/reference/adox-api/views-append-method-example-vb.md)   
 [Append-метод (коллекция Columns ADOX)](../../../ado/reference/adox-api/append-method-adox-columns.md)   
 [Append-метод (коллекция Groups ADOX)](../../../ado/reference/adox-api/append-method-adox-groups.md)   
 [Append-метод (коллекция Indexes ADOX)](../../../ado/reference/adox-api/append-method-adox-indexes.md)   
 [Append-метод (коллекция Keys ADOX)](../../../ado/reference/adox-api/append-method-adox-keys.md)   
 [Append-метод (коллекция Procedures ADOX)](../../../ado/reference/adox-api/append-method-adox-procedures.md)   
 [Append-метод (коллекция Tables ADOX)](../../../ado/reference/adox-api/append-method-adox-tables.md)   
 [Метод Append (коллекция Users ADOX)](../../../ado/reference/adox-api/append-method-adox-users.md)
