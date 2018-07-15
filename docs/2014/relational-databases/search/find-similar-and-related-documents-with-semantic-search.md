---
title: Поиск похожих и связанных документов с помощью семантического поиска | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: search
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- semantic search [SQL Server], document similarity queries
ms.assetid: 9f527883-031b-442f-8e95-24bc0151ecbf
caps.latest.revision: 17
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: b38cdb3e37ff8dca8a1fb206513c69a826ce91c2
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37319894"
---
# <a name="find-similar-and-related-documents-with-semantic-search"></a>Поиск похожих и связанных документов с использованием семантического поиска
  Описывает процесс поиска схожих или связанных документов или текстовых значений и сведений об их сходстве или связи в столбцах, настроенных для статистического семантического индексирования.  
  
##  <a name="BasicsQuerySimilar"></a> Поиск схожих или связанных документов  
  
###  <a name="HowToQuerySimilar"></a> Практическое руководство: Поиск схожих или связанных документов с помощью функции SEMANTICSIMILARITYTABLE  
 Чтобы найти схожие или связанные документы в данном столбце, запросите функцию [semanticsimilaritytable (Transact-SQL)](/sql/relational-databases/system-functions/semanticsimilaritytable-transact-sql).  
  
 Функция**SEMANTICSIMILARITYTABLE** возвращает таблицу, состоящую из нуля, одной или нескольких строк, содержимое которых в указанном столбце семантически схоже с заданным документом. На эту функцию набора строк можно ссылаться в предложении FROM инструкции SELECT как на обычное имя таблицы.  
  
 Искать схожие документы по разным столбцам невозможно. Функция **SEMANTICSIMILARITYTABLE** извлекает результаты только из столбца, совпадающего с исходным столбцом, определяемым аргументом **source_key**.  
  
 Подробные сведения о параметрах функции **SEMANTICSIMILARITYTABLE** и о возвращаемой таблице результатов см. в статье [semanticsimilaritytable (Transact-SQL)](/sql/relational-databases/system-functions/semanticsimilaritytable-transact-sql).  
  
> [!IMPORTANT]  
>  Для целевых столбцов должно быть включено полнотекстовое и семантическое индексирование.  
  
###  <a name="HowToIdentifySimilar"></a> Пример: Поиск наиболее важных документов, больше всего схожих с другим документом  
 В следующем примере извлекается до 10 кандидатов, подобных указанному кандидату, обозначенному *@CandidateID* из таблицы HumanResources.JobCandidate в образце базы данных AdventureWorks2012.  
  
```scr  
SELECT TOP(10) KEY_TBL.matched_document_key AS Candidate_ID  
FROM SEMANTICSIMILARITYTABLE  
    (  
    HumanResources.JobCandidate,  
    Resume,  
    @CandidateID  
    ) AS KEY_TBL  
ORDER BY KEY_TBL.score DESC;  
GO  
```  
  
##  <a name="BasicsQuerySimilarity"></a> Поиск сведений о документов схожими или связанными  
  
###  <a name="HowToQuerySimilarity"></a> Практическое руководство: Поиск сведений о документов схожими или связанными с помощью функции SEMANTICSIMILARITYDETAILSTABLE  
 Чтобы получить дополнительные сведения о ключевых фразах, которые делают документы схожими или связанными, вызовите функцию [semanticsimilaritydetailstable (Transact-SQL)](/sql/relational-databases/system-functions/semanticsimilaritydetailstable-transact-sql).  
  
 Функция **SEMANTICSIMILARITYDETAILSTABLE** возвращает таблицу из нуля, одной или нескольких строк с ключевыми фразами, общими для двух документов (исходного документа и сопоставленного документа), содержимое которых семантически схоже. На эту функцию набора строк можно ссылаться в предложении FROM инструкции SELECT как на обычное имя таблицы.  
  
 Подробные сведения о параметрах функции **SEMANTICSIMILARITYDETAILSTABLE** и о возвращаемой таблице результатов см. в статье [semanticsimilaritydetailstable (Transact-SQL)](/sql/relational-databases/system-functions/semanticsimilaritydetailstable-transact-sql).  
  
> [!IMPORTANT]  
>  Для целевых столбцов должно быть включено полнотекстовое и семантическое индексирование.  
  
###  <a name="HowToSimilarPhrases"></a> Пример: Поиск ключевых фраз, которые схожи в разных документах  
 В следующем примере производится извлечение 5 ключевых фраз, имеющих высший показатель подобия среди указанных кандидатов в таблице **HumanResources.JobCandidate** образца базы данных AdventureWorks2012.  
  
```tsql  
SELECT TOP(5) KEY_TBL.keyphrase, KEY_TBL.score  
FROM SEMANTICSIMILARITYDETAILSTABLE  
    (  
    HumanResources.JobCandidate,  
    Resume, @CandidateID,  
    Resume, @MatchedID  
    ) AS KEY_TBL  
ORDER BY KEY_TBL.score DESC;  
GO  
```  
  
  
