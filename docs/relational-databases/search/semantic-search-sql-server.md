---
title: Семантический поиск (SQL Server) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: search, sql-database
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
ms.openlocfilehash: 287ef0015b58e65e541ded8bc1a4200fed804814
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47755972"
---
# <a name="semantic-search-sql-server"></a>Семантический поиск (SQL Server)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
Статистический семантический поиск обеспечивает глубокий анализ неструктурированных документов, хранящихся в базах данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] путем извлечения и индексирования статистически соответствующих *ключевых фраз*. Эти ключевые фразы используются также для идентификации и индексирования *схожих или связанных документов*.  
  
##  <a name="whatcanido"></a>Что можно сделать с помощью семантического поиска?  
 Семантический поиск основан на существующей функции полнотекстового поиска в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], но дает новые возможности, выходящие за пределы поиска ключевых слов. Полнотекстовый поиск позволяет запрашивать *слова* в документе, а семантический поиск позволяет запрашивать *значение* документа. Среди новых возможностей автоматическое извлечение тегов, обнаружение связанного содержимого и иерархическая навигация по схожему содержимому. Например, можно запросить индекс ключевых фраз, чтобы создать классификацию для организации или совокупности документов. Или можно запросить индекс сходства документов для выявления резюме, соответствующих описанию вакансии.  
  
 Следующие примеры демонстрируют возможности семантического поиска. В то же время эти примеры демонстрируют три функции набора строк языка Transact-SQL, которые можно использовать для запроса семантических индексов и получения результатов в виде структурированных данных.  
  
###  <a name="find1"></a> Find the key phrases in a document  
 Следующий запрос получает ключевые фразы, которые были определены в образце документа. Он возвращает список результаты в порядке убывания показателя, обозначающего статистическую значимость каждой ключевой фразы.
 
 Этот запрос вызывает функцию [semantickeyphrasetable](../../relational-databases/system-functions/semantickeyphrasetable-transact-sql.md).  
  
```sql  
SET @Title = 'Sample Document.docx'  
  
SELECT @DocID = DocumentID  
    FROM Documents  
    WHERE DocumentTitle = @Title  
  
SELECT @Title AS Title, keyphrase, score  
    FROM SEMANTICKEYPHRASETABLE(Documents, *, @DocID)  
    ORDER BY score DESC  
  
```  
  
###  <a name="find2"></a> Find similar or related documents  
 Следующий запрос возвращает документы, которые были определены как схожие с образцом документа или связанные. Он возвращает результаты в порядке убывания показателя, обозначающего схожесть двух документов.
 
 Этот запрос вызывает функцию [semanticsimilaritytable](../../relational-databases/system-functions/semanticsimilaritytable-transact-sql.md).  
  
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
  
###  <a name="find3"></a> Find the key phrases that make documents similar or related  
 Следующий запрос возвращает ключевые фразы, которые делают два документа схожими или связанными. Он возвращает результаты в порядке убывания показателя, обозначающего вес каждой ключевой фразы.
 
 Этот запрос вызывает функцию [semanticsimilaritydetailstable](../../relational-databases/system-functions/semanticsimilaritydetailstable-transact-sql.md).  
  
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
  
 Функция FileTable в SQL Server делает неструктурированные файлы и документы первоклассным содержимым реляционной базы данных. С их помощью разработчики баз данных могут управлять документами вместе со структурированными данными с использованием набора операций Transact-SQL.  
  
 Дополнительные сведения о таблицах FileTable см. в статье [Таблицы FileTable (SQL Server)](../../relational-databases/blob/filetables-sql-server.md). Дополнительные сведения о функции FILESTREAM, являющейся еще одним вариантом сохранения документов в базе данных, см. в разделе [FILESTREAM (SQL Server)](../../relational-databases/blob/filestream-sql-server.md).  
  
##  <a name="reltasks"></a> Related tasks  
 [Установка и настройка семантического поиска](../../relational-databases/search/install-and-configure-semantic-search.md)  
 Описывает компоненты, необходимые для статистического семантического поиска, и способы их установки и проверки.  
  
 [Включение семантического поиска по таблицам и столбцам](../../relational-databases/search/enable-semantic-search-on-tables-and-columns.md)  
 Описывает способ включения или отключения статистического семантического индексирования в выбранных столбцах, содержащих документы или текст.  
  
 [Поиск ключевых фраз в документах с использованием семантического поиска](../../relational-databases/search/find-key-phrases-in-documents-with-semantic-search.md)  
 Описывает способ поиска ключевых фраз в документах или текстовых столбцах, настроенных для статистического семантического индексирования.  
  
 [Поиск похожих и связанных документов с использованием семантического поиска](../../relational-databases/search/find-similar-and-related-documents-with-semantic-search.md)  
 Описывает процесс поиска схожих или связанных документов или текстовых значений и сведений об их сходстве или связи в столбцах, настроенных для статистического семантического индексирования.  
  
 [Управление и наблюдение за семантическим поиском](../../relational-databases/search/manage-and-monitor-semantic-search.md)  
 Описывается процесс семантического индексирования и задачи, связанные с наблюдением за индексами и управлением ими.  
  
##  <a name="relcontent"></a> Related content  
 [Инструкции семантического поиска DDL, функции, хранимые процедуры и представления](../../relational-databases/search/semantic-search-ddl-functions-stored-procedures-and-views.md)  
 Содержит список инструкций Transact-SQL и объектов базы данных SQL Server, добавленных или измененных для поддержки статистического семантического поиска.  
  
  
