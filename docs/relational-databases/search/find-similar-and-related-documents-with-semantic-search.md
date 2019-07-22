---
title: Поиск похожих и связанных документов с помощью семантического поиска | Документация Майкрософт
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: search, sql-database
ms.technology: search
ms.topic: conceptual
helpviewer_keywords:
- semantic search [SQL Server], document similarity queries
ms.assetid: 9f527883-031b-442f-8e95-24bc0151ecbf
author: pmasl
ms.author: pelopes
ms.reviewer: mikeray
ms.openlocfilehash: 051e0a70bedaf7c7731b5f8cd0b9dfe91f078fea
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68082800"
---
# <a name="find-similar-and-related-documents-with-semantic-search"></a>Поиск похожих и связанных документов с использованием семантического поиска
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Описывает процесс поиска схожих или связанных документов или текстовых значений и сведений об их сходстве или связи в столбцах, настроенных для статистического семантического индексирования.  
   
##  <a name="HowToQuerySimilar"></a> Поиск похожих и связанных документов с помощью SEMANTICSIMILARITYTABLE  
 Чтобы найти схожие или связанные документы в данном столбце, запросите функцию [semanticsimilaritytable (Transact-SQL)](../../relational-databases/system-functions/semanticsimilaritytable-transact-sql.md).  
  
 Функция**SEMANTICSIMILARITYTABLE** возвращает таблицу, состоящую из нуля, одной или нескольких строк, содержимое которых в указанном столбце семантически схоже с заданным документом. На эту функцию набора строк можно ссылаться в предложении FROM инструкции SELECT как на обычное имя таблицы.  
  
 Искать схожие документы по разным столбцам невозможно. Функция **SEMANTICSIMILARITYTABLE** извлекает результаты только из столбца, совпадающего с исходным столбцом, определяемым аргументом **source_key**.  
  
 Подробные сведения о параметрах функции **SEMANTICSIMILARITYTABLE** и о возвращаемой таблице результатов см. в статье [semanticsimilaritytable (Transact-SQL)](../../relational-databases/system-functions/semanticsimilaritytable-transact-sql.md).  
  
> [!IMPORTANT]  
>  Для целевых столбцов должно быть включено полнотекстовое и семантическое индексирование.  
  
###  <a name="HowToIdentifySimilar"></a> Пример. Поиск наиболее важных документов, больше всего схожих с другим документом  
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
  
##  <a name="HowToQuerySimilarity"></a>Узнайте, как правильно искать сведения о схожести или связи документов с помощью функции SEMANTICSIMILARITYDETAILSTABLE  
 Чтобы получить дополнительные сведения о ключевых фразах, которые делают документы схожими или связанными, вызовите функцию [semanticsimilaritydetailstable (Transact-SQL)](../../relational-databases/system-functions/semanticsimilaritydetailstable-transact-sql.md).  
  
 Функция **SEMANTICSIMILARITYDETAILSTABLE** возвращает таблицу из нуля, одной или нескольких строк с ключевыми фразами, общими для двух документов (исходного документа и сопоставленного документа), содержимое которых семантически схоже. На эту функцию набора строк можно ссылаться в предложении FROM инструкции SELECT как на обычное имя таблицы.  
  
 Подробные сведения о параметрах функции **SEMANTICSIMILARITYDETAILSTABLE** и о возвращаемой таблице результатов см. в статье [semanticsimilaritydetailstable (Transact-SQL)](../../relational-databases/system-functions/semanticsimilaritydetailstable-transact-sql.md).  
  
> [!IMPORTANT]  
>  Для целевых столбцов должно быть включено полнотекстовое и семантическое индексирование.  
  
###  <a name="HowToSimilarPhrases"></a> Пример. Поиск ключевых фраз, которые больше всего схожи в разных документах  
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
  
  
