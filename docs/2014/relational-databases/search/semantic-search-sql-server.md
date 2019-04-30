---
title: Семантический поиск (SQL Server) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
helpviewer_keywords:
- semantic search [SQL Server]
- semantic search [SQL Server], overview
- statistical semantic search [SQL Server]
- statistical semantic search [SQL Server], overview
ms.assetid: cd8faa9d-07db-420d-93f4-a2ea7c974b97
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: ea08ef15d62f2897fdba5a966d43a639a3fc1efe
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63238647"
---
# <a name="semantic-search-sql-server"></a>Семантический поиск (SQL Server)
  Статистический семантический поиск обеспечивает глубокий анализ неструктурированных документов, хранящихся в базах данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] путем извлечения и индексирования статистически соответствующих *ключевых фраз*. Эти ключевые фразы используются также для идентификации и индексирования *схожих или связанных документов*.  
  
 Запросы к этим семантическим индексам создаются с помощью трех функций наборов строк языка Transact-SQL для получения результатов в виде структурированных данных.  
  
##  <a name="whatcanido"></a> Что можно сделать с помощью семантического поиска?  
 Семантический поиск основан на существующей функции полнотекстового поиска в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], но дает новые возможности, выходящие за пределы поиска ключевых слов. Полнотекстовый поиск позволяет запрашивать *слова* в документе, а семантический поиск позволяет запрашивать *значение* документа. Среди новых возможностей автоматическое извлечение тегов, обнаружение связанного содержимого и иерархическая навигация по схожему содержимому. Например, можно запросить индекс ключевых фраз, чтобы создать классификацию для организации или совокупности документов. Или можно запросить индекс сходства документов для выявления резюме, соответствующих описанию вакансии.  
  
 Следующие примеры демонстрируют возможности семантического поиска.  
  
###  <a name="find1"></a> Найти ключевые фразы в документе  
 Следующий запрос получает ключевые фразы, которые были определены в образце документа. Он возвращает список результаты в порядке убывания показателя, обозначающего статистическую значимость каждой ключевой фразы. Этот запрос вызывает функцию [semantickeyphrasetable (Transact-SQL)](/sql/relational-databases/system-functions/semantickeyphrasetable-transact-sql).  
  
```sql  
SET @Title = 'Sample Document.docx'  
  
SELECT @DocID = DocumentID  
    FROM Documents  
    WHERE DocumentTitle = @Title  
  
SELECT @Title AS Title, keyphrase, score  
    FROM SEMANTICKEYPHRASETABLE(Documents, *, @DocID)  
    ORDER BY score DESC  
  
```  
  
  
  
###  <a name="find2"></a> Поиск схожих или связанных документов  
 Следующий запрос возвращает документы, которые были определены как схожие с образцом документа или связанные. Он возвращает результаты в порядке убывания показателя, обозначающего схожесть двух документов. Этот запрос вызывает функцию [semanticsimilaritytable (Transact-SQL)](/sql/relational-databases/system-functions/semanticsimilaritytable-transact-sql).  
  
```vb  
SET @Title = 'Sample Document.docx'  
  
SELECT @DocID = DocumentID  
    FROM Documents  
    WHERE DocumentTitle = @Title  
  
SELECT @Title AS SourceTitle, DocumentTitle AS MatchedTitle,  
        DocumentID, score  
    FROM SEMANTICSIMILARITYTABLE(Documents, *, @DocID)  
    INNER JOIN Documents ON DocumentID = matched_document_key  
    ORDER BY score DESC  
  
```  
  
  
  
###  <a name="find3"></a> Найти ключевые фразы, делающие документы схожими или связанными  
 Следующий запрос возвращает ключевые фразы, которые делают два документа схожими или связанными. Он возвращает результаты в порядке убывания показателя, обозначающего вес каждой ключевой фразы. Этот запрос вызывает функцию [semanticsimilaritydetailstable (Transact-SQL)](/sql/relational-databases/system-functions/semanticsimilaritydetailstable-transact-sql).  
  
```sql  
SET @SourceTitle = 'first.docx'  
SET @MatchedTitle = 'second.docx'  
  
SELECT @SourceDocID = DocumentID FROM Documents WHERE DocumentTitle = @SourceTitle  
SELECT @MatchedDocID = DocumentID FROM Documents WHERE DocumentTitle = @MatchedTitle  
  
SELECT @SourceTitle AS SourceTitle, @MatchedTitle AS MatchedTitle, keyphrase, score  
    FROM semanticsimilaritydetailstable(Documents, DocumentContent,  
        @SourceDocID, DocumentContent, @MatchedDocID)  
    ORDER BY score DESC  
  
```  
  
  
  
##  <a name="store"></a> Хранение документов в SQL Server  
 Прежде чем индексировать документы с семантическим поиском, необходимо сохранить их в базе данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 Функция FileTable в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] делает неструктурированные файлы и документы первоклассным содержимым реляционной базы данных. С их помощью разработчики баз данных могут управлять документами вместе со структурированными данными с использованием набора операций Transact-SQL.  
  
 Дополнительные сведения о таблицах FileTable см. в разделе [Таблицы FileTable (SQL Server)](../blob/filetables-sql-server.md). Дополнительные сведения о функции FILESTREAM, являющейся еще одним вариантом сохранения документов в базе данных, см. в разделе [FILESTREAM (SQL Server)](../blob/filestream-sql-server.md).  
  
  
  
##  <a name="reltasks"></a> Связанные задачи  
 [Установка и настройка семантического поиска](install-and-configure-semantic-search.md)  
 Описывает компоненты, необходимые для статистического семантического поиска, и способы их установки и проверки.  
  
 [Включение семантического поиска по таблицам и столбцам](enable-semantic-search-on-tables-and-columns.md)  
 Описывает способ включения или отключения статистического семантического индексирования в выбранных столбцах, содержащих документы или текст.  
  
 [Поиск ключевых фраз в документах с использованием семантического поиска](find-key-phrases-in-documents-with-semantic-search.md)  
 Описывает способ поиска ключевых фраз в документах или текстовых столбцах, настроенных для статистического семантического индексирования.  
  
 [Поиск похожих и связанных документов с использованием семантического поиска](find-similar-and-related-documents-with-semantic-search.md)  
 Описывает процесс поиска схожих или связанных документов или текстовых значений и сведений об их сходстве или связи в столбцах, настроенных для статистического семантического индексирования.  
  
 [Управление и наблюдение за семантическим поиском](manage-and-monitor-semantic-search.md)  
 Описывается процесс семантического индексирования и задачи, связанные с наблюдением за индексами и управлением ими.  
  
##  <a name="relcontent"></a> См. также  
 [Инструкции DDL, функции, хранимые процедуры и представления для семантического поиска](../views/views.md)  
 Содержит список инструкций Transact-SQL и объектов базы данных SQL Server, добавленных или измененных для поддержки статистического семантического поиска.  
  
  
