---
title: Поиск ключевых фраз в документах с использованием семантического поиска | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-search
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- semantic search [SQL Server], key phrase queries
ms.assetid: 6ee3676e-ed5d-43ec-aeca-1eed78967111
caps.latest.revision: 16
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 28696617406fd5f3776181a79cd8fb84bec04307
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36110121"
---
# <a name="find-key-phrases-in-documents-with-semantic-search"></a>Поиск ключевых фраз в документах с использованием семантического поиска
  Описывает способ поиска ключевых фраз в документах или текстовых столбцах, настроенных для статистического семантического индексирования.  
  
##  <a name="BasicsQueryKey"></a> Поиск ключевых фраз в документах  
  
###  <a name="howtofind"></a> Как: поиск ключевых фраз в документах с помощью SEMANTICKEYPHRASETABLE  
 Для поиска ключевых фраз в определенных документах или для поиска документов, содержащих определенные ключевые фразы, можно запросить функцию [semantickeyphrasetable (Transact-SQL)](/sql/relational-databases/system-functions/semantickeyphrasetable-transact-sql).  
  
 Функция SEMANTICKEYPHRASETABLE возвращает таблицу с нулем, одной или несколькими строками для ключевых фраз, связанных со столбцами в указанной таблице. На эту функцию набора строк можно ссылаться из предложения FROM инструкции SELECT так же, как и на обычное имя таблицы.  
  
> [!NOTE]  
>  В [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]только отдельные слова индексируются для семантического поиска. Фразы из нескольких слов (n-граммы) не индексируются. Кроме того, различные формы одного и того же слова индексируются отдельно. Например, «компьютер» и «компьютеры» индексируются отдельно.  
  
 Подробные сведения о параметрах, необходимых для функции SEMANTICKEYPHRASETABLE, и о таблице возвращаемых ей результатов см. в разделе [semantickeyphrasetable (Transact-SQL)](/sql/relational-databases/system-functions/semantickeyphrasetable-transact-sql).  
  
> [!IMPORTANT]  
>  Для целевых столбцов должно быть включено полнотекстовое и семантическое индексирование.  
  
###  <a name="HowToTopPhrases"></a> Пример 1: Поиск ключевых фраз в определенном документе  
 В следующем примере извлекаются 10 первых ключевых фраз из документа, указанного в переменной @DocumentId в столбце Document таблицы Production.Document в тестовой базе данных AdventureWorks. Переменная @DocumentId представляет значение из ключевого столбца полнотекстового индекса.  
  
```tsql  
SELECT TOP(10) KEYP_TBL.keyphrase  
FROM SEMANTICKEYPHRASETABLE  
    (  
    Production.Document,  
    Document,  
    @DocumentId  
    ) AS KEYP_TBL  
ORDER BY KEYP_TBL.score DESC;  
GO  
```  
  
 Функция **SEMANTICKEYPHRASETABLE** эффективно извлекает эти результаты поиском по индексу, а не путем просмотра таблицы.  
  
###  <a name="HowToTopDocuments"></a> Пример 2: Поиск наиболее важных документов, содержащих определенную ключевую фразу  
 В следующем примере извлекаются 25 первых документов, содержащих ключевую фразу «Bracket» в столбце «Document» таблицы Production.Document образца базы данных AdventureWorks.  
  
```tsql  
SELECT TOP (25) DOC_TBL.DocumentID, DOC_TBL.DocumentSummary  
FROM Production.Document AS DOC_TBL  
    INNER JOIN SEMANTICKEYPHRASETABLE  
    (  
    Production.Document,  
    Document  
    ) AS KEYP_TBL  
ON DOC_TBL.DocumentID = KEYP_TBL.document_key  
WHERE KEYP_TBL.keyphrase = 'Bracket'  
ORDER BY KEYP_TBL.Score DESC;  
GO  
```  
  
  
