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
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 266687488dbd12b504b079314cc9d07b801b4f28
ms.sourcegitcommit: 4b5919e3ae5e252f8d6422e8e6fddac1319075a1
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/09/2020
ms.locfileid: "83000864"
---
# <a name="full-text-stoplist-properties"></a>Свойства полнотекстового списка стоп-слов
  Это диалоговое окно используется для добавления и удаления отдельных стоп-слов, удаления всех стоп-слов указанного языка, а также для очистки текущего списка стоп-слов. Стоп-слово — это часто употребляемое слово, включенное в список стоп-слов. Стоп-слова из этого списка исключаются при полнотекстовом индексировании таблиц, в которых используется список стоп-слов. Дополнительные сведения см. в разделе [Настройка стоп-слов и списков стоп-слов для полнотекстового поиска и управление ими](../relational-databases/search/full-text-search.md).  
  
 **Изменение свойств списка стоп-слов в среде SQL Server Management Studio**  
  
-   [Настройка и управление стоп-словами и списками стоп-слов для полнотекстового поиска](../relational-databases/search/full-text-search.md)  
  
## <a name="options"></a>Параметры  
 **Действие**  
 Указывает действие, которое необходимо выполнить.  
  
 **Добавить стоп-слово**  
 Добавление в список стоп-слов часто употребляемого слова.  
  
 **Удалить стоп-слово**  
 Удаление стоп-слова из списка.  
  
 **Удалить все стоп-слова**  
 Удаление всех стоп-слов определенного языка.  
  
 **Очистить список стоп-слов**  
 Очистка списка путем удаления всех стоп-слов всех языков.  
  
 **Стоп-слово**  
 Если выбрана команда **Добавить стоп-слово** или **Удалить стоп-слово**, введите это слово в поле **Стоп-слово** . Новое стоп-слово должно быть уникальным, то есть отсутствовать в списке стоп-слов для выбранного языка.  
  
 **Язык полнотекстового поиска**  
 Если выбрана команда **Добавить стоп-слово**, **Удалить стоп-слово**или **Удалить все стоп-слова**, выберите язык стоп-слов из списка. Список содержит все языки полнотекстового поиска, поддерживаемые экземпляром сервера.  
  
## <a name="see-also"></a>См. также  
 [sys. fulltext_stopwords &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-fulltext-stopwords-transact-sql)   
 [sys. fulltext_stoplists &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-fulltext-stoplists-transact-sql)   
 [Настройка стоп-слова и списков для полнотекстового поиска и управление ими](../relational-databases/search/full-text-search.md)   
 [ALTER FULLTEXT стоп-слов &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-fulltext-stoplist-transact-sql)   
 [Создание ПОЛНОТЕКСТОВОГО списка стоп-слов &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-fulltext-stoplist-transact-sql)   
 [DROP FULLTEXT STOPLIST (Transact-SQL)](/sql/t-sql/statements/drop-fulltext-stoplist-transact-sql)  
  
  
