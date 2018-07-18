---
title: Новый полнотекстовый список стоп-слов (страница "Общие") | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: search
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.fulltextsearch.ftstoplist.general.f1
ms.assetid: 97f8e82d-82ab-4525-91c9-1ee3ae217309
caps.latest.revision: 16
author: craigg-msft
ms.author: craigg
manager: craigg
ms.openlocfilehash: 2304b2b9a8711210117ffbb2a84abbf167694e71
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37221974"
---
# <a name="new-full-text-stoplist-general-page"></a>Создание списка полнотекстовых стоп-слов (страница «Общие»)
  Используется для создания полнотекстового списка стоп-слов. *Список стоп-слов* — это набор часто употребляемых слов, называемых *стоп-словами*, которые не включаются в полнотекстовый индекс для таблиц, использующих такой список. Дополнительные сведения см. в разделе [Настройка стоп-слов и списков стоп-слов для полнотекстового поиска и управление ими](../relational-databases/search/full-text-search.md).  
  
 **Использование SQL Server Management Studio для создания списка стоп-слов**  
  
-   [Настройка стоп-слов, списков стоп-слов и управление ими для полнотекстового поиска](../relational-databases/search/full-text-search.md)  
  
## <a name="options"></a>Параметры  
 **Имя списка стоп-слов полнотекстового поиска**  
 Введите имя полнотекстового списка стоп-слов.  
  
 **Владелец**  
 Укажите владельца полнотекстового списка стоп-слов. Чтобы сделать владельцем текущего пользователя, оставьте это поле пустым.  
  
 Чтобы указать другого пользователя, нажмите кнопку обзора.  
  
### <a name="create-stoplist-options"></a>Параметры создания списка стоп-слов  
 Выберите один из следующих вариантов.  
  
 **Создать пустой список стоп-слов**  
 Новый список не будет содержать стоп-слов.  
  
 **Создать из системного списка стоп-слов**  
 Новый список стоп-слов создается на основе списка, существующего в базе данных [Resource](../relational-databases/databases/resource-database.md)по умолчанию.  
  
 **Создать из существующего полнотекстового списка стоп-слов**  
 Новый список стоп-слов создается путем копирования существующего.  
  
 **Базы данных-источника**  
 Указывает имя базы данных, которой принадлежит существующий список стоп-слов. По умолчанию выбрана текущая база данных. При необходимости можно выбрать из списка другую базу данных.  
  
 **Источник списка стоп-слов**  
 Указывает имя существующего списка стоп-слов. Из перечня доступных списков выберите один, который будет использоваться в качестве источника. Доступные списки стоп-слов перечисляются в порядке их отображения в обозревателе объектов.  
  
 Если в текущей базе данных не зарегистрирован любой язык стоп-слов из исходного списка стоп-слов, инструкция CREATE FULLTEXT STOPLIST завершается успешно, но с предупреждениями, а соответствующие стоп-слова не добавляются.  
  
## <a name="see-also"></a>См. также  
 [ALTER FULLTEXT STOPLIST (Transact-SQL)](/sql/t-sql/statements/alter-fulltext-stoplist-transact-sql)   
 [CREATE FULLTEXT STOPLIST (Transact-SQL)](/sql/t-sql/statements/create-fulltext-stoplist-transact-sql)   
 [DROP FULLTEXT STOPLIST (Transact-SQL)](/sql/t-sql/statements/drop-fulltext-stoplist-transact-sql)   
 [Настройка стоп-слов, списков стоп-слов и управление ими для полнотекстового поиска](../relational-databases/search/full-text-search.md)   
 [sys.fulltext_stoplists (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-fulltext-stoplists-transact-sql)  
  
  
