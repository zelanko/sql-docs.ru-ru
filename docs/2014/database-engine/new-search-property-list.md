---
title: Новый список свойств поиска | Документы Microsoft
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-search
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.swb.spl.newsearchpropertylist.f1
ms.assetid: ffca78e9-8608-4b15-bd38-b2d78da4247a
caps.latest.revision: 21
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: b9d37bad141f61ceadafc03d883f36f422965996
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36194773"
---
# <a name="new-search-property-list"></a>Новый список свойств поиска
  Это диалоговое окно используется для создания списка свойств поиска.  
  
## <a name="options"></a>Параметры  
 **Имя списка свойств поиска**  
 Введите имя списка свойств поиска.  
  
 **Владелец**  
 Укажите владельца списка свойств поиска. Чтобы сделать владельцем текущего пользователя, оставьте это поле пустым. Чтобы указать другого пользователя, нажмите кнопку обзора.  
  
### <a name="create-search-property-list-options"></a>Параметры создания списка свойств поиска  
 Выберите один из следующих параметров:  
  
 **Создание пустого списка свойств поиска**  
 Создает список свойств поиска без свойств.  
  
 **Создание на основе существующего списка свойств поиска**  
 Копирует свойства существующего списка свойств поиска в новый список свойств. Списки свойств поиска — это защищаемые объекты базы данных, поэтому необходимо указать базу данных, содержащую список свойств, который нужно копировать.  
  
 **База данных-источник**  
 Укажите имя базы данных, которой принадлежит существующий список свойств поиска. По умолчанию выбрана текущая база данных. При необходимости можно использовать список для выбора другой базы данных, если текущее соединение связано с идентификатором пользователя в базе данных.  
  
 **Исходный список свойств поиска**  
 Выберите имя существующего списка свойств поиска из тех, которые принадлежат выбранной базе данных.  
  
## <a name="permissions"></a>Разрешения  
 В разделе [Создание СПИСКА СВОЙСТВ поиска &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-search-property-list-transact-sql).  
  
## <a name="to-use-sql-server-management-studio-to-manage-search-property-lists"></a>Управление списками свойств поиска в среде SQL Server Management Studio  
 Сведения о том, как создать, просмотреть, изменить или удалить список свойств поиска, а также о настройке полнотекстового индекса для поиска свойств см. в разделе [поиск свойств документа с использованием списков свойств поиска](../relational-databases/search/search-document-properties-with-search-property-lists.md).  
  
## <a name="see-also"></a>См. также  
 [CREATE SEARCH PROPERTY LIST (Transact-SQL)](/sql/t-sql/statements/create-search-property-list-transact-sql)   
 [Поиск свойств документа с использованием списков свойств поиска](../relational-databases/search/search-document-properties-with-search-property-lists.md)   
 [sys.registered_search_property_lists (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-registered-search-property-lists-transact-sql)  
  
  
