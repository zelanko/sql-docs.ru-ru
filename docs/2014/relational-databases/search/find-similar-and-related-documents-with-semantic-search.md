---
title: Поиск похожих и связанных документов с помощью семантического поиска | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
helpviewer_keywords:
- semantic search [SQL Server], document similarity queries
ms.assetid: 9f527883-031b-442f-8e95-24bc0151ecbf
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 1b2e30534fb5e0232ff2046e30e2e14075dfb807
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "66011321"
---
# <a name="find-similar-and-related-documents-with-semantic-search"></a>Поиск похожих и связанных документов с использованием семантического поиска
  Описывает процесс поиска схожих или связанных документов или текстовых значений и сведений об их сходстве или связи в столбцах, настроенных для статистического семантического индексирования.  
  
##  <a name="BasicsQuerySimilar"></a>Поиск схожих или связанных документов  
  
###  <a name="HowToQuerySimilar"></a>Как найти похожие или связанные документы с помощью SEMANTICSIMILARITYTABLE  
 Чтобы найти схожие или связанные документы в данном столбце, запросите функцию [semanticsimilaritytable (Transact-SQL)](/sql/relational-databases/system-functions/semanticsimilaritytable-transact-sql).  
  
 **SEMANTICSIMILARITYTABLE** возвращает таблицу из нуля, одну или несколько строк, содержимое которых в указанном столбце семантически аналогично указанному документу. На эту функцию набора строк можно ссылаться в предложении FROM инструкции SELECT как на обычное имя таблицы.  
  
 Искать схожие документы по разным столбцам невозможно. Функция **SEMANTICSIMILARITYTABLE** извлекает результаты только из столбца, совпадающего с исходным столбцом, определяемым аргументом **source_key**.  
  
 Подробные сведения о параметрах функции **SEMANTICSIMILARITYTABLE** и о возвращаемой таблице результатов см. в статье [semanticsimilaritytable (Transact-SQL)](/sql/relational-databases/system-functions/semanticsimilaritytable-transact-sql).  
  
> [!IMPORTANT]  
>  Для целевых столбцов должно быть включено полнотекстовое и семантическое индексирование.  
  
###  <a name="HowToIdentifySimilar"></a>Пример. Поиск лучших документов, которые похожи на другой документ  
 В следующем примере извлекаются 10 лучших кандидатов, которые похожи на кандидат, указанный *@CandidateID* в таблице HumanResources. JobCandidate в образце базы данных AdventureWorks2012.  
  
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
  
##  <a name="BasicsQuerySimilarity"></a>Поиск сведений о схожих и связанных документах  
  
###  <a name="HowToQuerySimilarity"></a>Инструкции. Поиск сведений о том, как документы похожи или связаны с SEMANTICSIMILARITYDETAILSTABLE  
 Чтобы получить дополнительные сведения о ключевых фразах, которые делают документы схожими или связанными, вызовите функцию [semanticsimilaritydetailstable (Transact-SQL)](/sql/relational-databases/system-functions/semanticsimilaritydetailstable-transact-sql).  
  
 **SEMANTICSIMILARITYDETAILSTABLE** возвращает таблицу из нуля, одну или несколько строк ключевых фраз, общих для двух документов (исходный документ и сопоставленный документ), содержимое которых семантически аналогично. На эту функцию набора строк можно ссылаться в предложении FROM инструкции SELECT как на обычное имя таблицы.  
  
 Подробные сведения о параметрах функции **SEMANTICSIMILARITYDETAILSTABLE** и о возвращаемой таблице результатов см. в статье [semanticsimilaritydetailstable (Transact-SQL)](/sql/relational-databases/system-functions/semanticsimilaritydetailstable-transact-sql).  
  
> [!IMPORTANT]  
>  Для целевых столбцов должно быть включено полнотекстовое и семантическое индексирование.  
  
###  <a name="HowToSimilarPhrases"></a>Пример. Поиск основных ключевых фраз, которые похожи на документы  
 В следующем примере производится извлечение 5 ключевых фраз, имеющих высший показатель подобия среди указанных кандидатов в таблице **HumanResources.JobCandidate** образца базы данных AdventureWorks2012.  
  
```sql  
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
  
  
