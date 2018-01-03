---
title: "Append-метод (ADOX представления) | Документы Microsoft"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- Views::raw_Append
- Views::Append
helpviewer_keywords: Append method [ADOX]
ms.assetid: 6070fd58-3237-4c77-a966-5b39ce5d57e4
caps.latest.revision: "12"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: acb0a9ffbf26ccb0f181e19c54ac906ae7d4754f
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="append-method-adox-views"></a>Append-метод (ADOX представления)
Создает новый [представление](../../../ado/reference/adox-api/view-object-adox.md) объекта и добавляет его к [представления](../../../ado/reference/adox-api/views-collection-adox.md) коллекции.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Views.Append Name, Command  
```  
  
#### <a name="parameters"></a>Параметры  
 *Название*  
 Объект **строка** значение, указывающее имя представления.  
  
 *Command*  
 ADO [команда](../../../ado/reference/ado-api/command-object-ado.md) , отражающий представление для создания объекта.  
  
## <a name="remarks"></a>Remarks  
 Создает новое представление источника данных с именем и атрибутами, заданными в **команда** объекта.  
  
 Если текст команды, который пользователь указывает представляет процедуру, а не представление, поведение зависит от поставщика. **Добавление** завершится ошибкой, если поставщик не поддерживает сохранение команды.  
  
> [!NOTE]
>  При использовании поставщика OLE DB для Microsoft Jet **представления** коллекции **Append** метод дает возможность указать **процедура** вместо **представление**  в *команда* параметра. **Процедура** и добавляются к источнику данных будут добавлены **представления** коллекции. После **Append**, если **процедуры** и **представления** обновляются коллекций, **процедура** больше не будет в **Представления** коллекции и будет отображаться в **процедуры** коллекции.  
  
## <a name="applies-to"></a>Объект применения  
 [Коллекция Views (ADOX)](../../../ado/reference/adox-api/views-collection-adox.md)  
  
## <a name="see-also"></a>См. также:  
 [Представления Append пример метода (Visual Basic)](../../../ado/reference/adox-api/views-append-method-example-vb.md)   
 [Append-метод (ADOX столбцы)](../../../ado/reference/adox-api/append-method-adox-columns.md)   
 [Append-метод (ADOX группы)](../../../ado/reference/adox-api/append-method-adox-groups.md)   
 [Append-метод (ADOX индексы)](../../../ado/reference/adox-api/append-method-adox-indexes.md)   
 [Append-метод (ADOX ключи)](../../../ado/reference/adox-api/append-method-adox-keys.md)   
 [Append-метод (ADOX процедур)](../../../ado/reference/adox-api/append-method-adox-procedures.md)   
 [Append-метод (ADOX таблицы)](../../../ado/reference/adox-api/append-method-adox-tables.md)   
 [Метод Append (коллекция Users ADOX)](../../../ado/reference/adox-api/append-method-adox-users.md)
