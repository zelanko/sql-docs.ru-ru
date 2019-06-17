---
title: Свойства полнотекстового списка стоп-слов | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
f1_keywords:
- sql12.swb.fulltextsearch.ftstoplistproperties.general.f1
- sql12.swb.fulltextsearch.ftstoplistproperties.schedule.f1
ms.assetid: 2e907f5b-0cf9-484a-afcf-a4e7f1e2f87f
author: craigg-msft
ms.author: craigg
manager: craigg
ms.openlocfilehash: 4cfdd308ab7488633721ddaac55d3d926a276b0d
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "62779411"
---
# <a name="full-text-stoplist-properties"></a>Свойства полнотекстового списка стоп-слов
  Это диалоговое окно используется для добавления и удаления отдельных стоп-слов, удаления всех стоп-слов указанного языка, а также для очистки текущего списка стоп-слов. Стоп-слово — это часто употребляемое слово, включенное в список стоп-слов. Стоп-слова из этого списка исключаются при полнотекстовом индексировании таблиц, в которых используется список стоп-слов. Дополнительные сведения см. в разделе [Настройка стоп-слов и списков стоп-слов для полнотекстового поиска и управление ими](../relational-databases/search/full-text-search.md).  
  
 **Чтобы использовать SQL Server Management Studio для изменения свойств списка стоп-слов**  
  
-   [Настройка стоп-слов, списков стоп-слов и управление ими для полнотекстового поиска](../relational-databases/search/full-text-search.md)  
  
## <a name="options"></a>Параметры  
 **Действие**  
 Указывает действие, которое необходимо выполнить.  
  
 **Добавить стоп-слово**  
 Добавление в список стоп-слов часто употребляемого слова.  
  
 **Удалить стоп-слово**  
 Удаление стоп-слова из списка.  
  
 **Удалить все Стоп-слова**  
 Удаление всех стоп-слов определенного языка.  
  
 **Очистить список стоп-слов**  
 Очистка списка путем удаления всех стоп-слов всех языков.  
  
 **Стоп-слово**  
 Если выбрана команда **Добавить стоп-слово** или **Удалить стоп-слово**, введите это слово в поле **Стоп-слово** . Новое стоп-слово должно быть уникальным, то есть отсутствовать в списке стоп-слов для выбранного языка.  
  
 **Язык полнотекстового поиска**  
 Если выбрана команда **Добавить стоп-слово**, **Удалить стоп-слово**или **Удалить все стоп-слова**, выберите язык стоп-слов из списка. Список содержит все языки полнотекстового поиска, поддерживаемые экземпляром сервера.  
  
## <a name="see-also"></a>См. также  
 [sys.fulltext_stopwords (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-fulltext-stopwords-transact-sql)   
 [sys.fulltext_stoplists (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-fulltext-stoplists-transact-sql)   
 [Настройка стоп-слов, списков стоп-слов и управление ими для полнотекстового поиска](../relational-databases/search/full-text-search.md)   
 [ALTER FULLTEXT STOPLIST (Transact-SQL)](/sql/t-sql/statements/alter-fulltext-stoplist-transact-sql)   
 [CREATE FULLTEXT STOPLIST (Transact-SQL)](/sql/t-sql/statements/create-fulltext-stoplist-transact-sql)   
 [DROP FULLTEXT STOPLIST (Transact-SQL)](/sql/t-sql/statements/drop-fulltext-stoplist-transact-sql)  
  
  
