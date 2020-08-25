---
description: Объекты ADOX
title: Объекты ADOX | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- objects [ADOX]
- ADOX, objects
ms.assetid: 3f5287e9-f62c-40c4-bb59-985102be956e
author: rothja
ms.author: jroth
ms.openlocfilehash: ca5131235b4c34c05f4cc3b783087f25dc027e95
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/24/2020
ms.locfileid: "88771583"
---
# <a name="adox-objects"></a>Объекты ADOX
## <a name="adox-object-summary"></a>Сводка объекта ADOX  
  
|Объект|Описание|  
|------------|-----------------|  
|[Каталог](./catalog-object-adox.md)|Содержит коллекции, описывающие каталог схем источника данных.|  
|[Столбец](./column-object-adox.md)|Представляет столбец из таблицы, индекса или ключа.|  
|[Группа](./group-object-adox.md)|Представляет учетную запись группы, имеющую разрешения на доступ в защищенной базе данных.|  
|[Index](./index-object-adox.md)|Представляет индекс из таблицы базы данных.|  
|[Key](./key-object-adox.md)|Представляет первичное, внешнее или уникальное ключевое поле из таблицы базы данных.|  
|[PROCEDURE](./procedure-object-adox.md)|Представляет хранимую процедуру.|  
|[Таблица](./table-object-adox.md)|Представляет таблицу базы данных, включая столбцы, индексы и ключи.|  
|[Пользователь](./user-object-adox.md)|Представляет учетную запись пользователя, имеющую разрешения на доступ в защищенной базе данных.|  
|[Просмотр](./view-object-adox.md)|Представляет отфильтрованный набор записей или виртуальную таблицу.|  
  
 Связи между этими объектами иллюстрируются в [объектной модели ADOX](./adox-object-model.md).  
  
 Каждый объект может содержаться в соответствующей коллекции. Например, объект **таблицы** может содержаться в коллекции [таблиц](./tables-collection-adox.md) . Дополнительные сведения см. в разделах [ADOX Collections](./adox-collections.md) или специальный набор разделов.  
  
## <a name="see-also"></a>См. также  
 [Справочник по API ADOX](./adox-object-model.md?view=sql-server-ver15)   
 [ADOX коллекции](./adox-collections.md)   
 [Объектная модель ADOX](./adox-object-model.md)   
 [Расширения ADO для языка описания данных и безопасности (ADOX)](../../guide/extensions/ado-extensions-for-data-definition-language-and-security-adox.md)