---
description: Поиск ключевых фраз в документах с использованием семантического поиска
title: Поиск ключевых фраз в документах с использованием семантического поиска
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: search, sql-database
ms.technology: search
ms.topic: conceptual
helpviewer_keywords:
- semantic search [SQL Server], key phrase queries
ms.assetid: 6ee3676e-ed5d-43ec-aeca-1eed78967111
author: pmasl
ms.author: pelopes
ms.reviewer: mikeray
ms.custom: seo-lt-2019
ms.openlocfilehash: 62a0ba559733c42ddf25b5d40896c4e53bdcf7b7
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88490587"
---
# <a name="find-key-phrases-in-documents-with-semantic-search"></a>Поиск ключевых фраз в документах с использованием семантического поиска
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  Описывает способ поиска ключевых фраз в документах или текстовых столбцах, настроенных для статистического семантического индексирования.  

##  <a name="find-the-key-phrases-in-documents-with-semantickeyphrasetable"></a><a name="howtofind"></a> Поиск ключевых фраз в документах с помощью SEMANTICKEYPHRASETABLE  
 Для поиска ключевых фраз в определенных документах или для поиска документов, содержащих определенные ключевые фразы, можно запросить функцию [semantickeyphrasetable (Transact-SQL)](../../relational-databases/system-functions/semantickeyphrasetable-transact-sql.md).  
  
 Функция SEMANTICKEYPHRASETABLE возвращает таблицу с нулем, одной или несколькими строками для ключевых фраз, связанных со столбцами в указанной таблице. На эту функцию набора строк можно ссылаться из предложения FROM инструкции SELECT так же, как и на обычное имя таблицы.  
  
> [!NOTE]  
>  В этом выпуске для семантического поиска индексируются только отдельные слова. Фразы из нескольких слов (n-граммы) не индексируются. Кроме того, различные формы одного и того же слова индексируются отдельно. Например, «компьютер» и «компьютеры» индексируются отдельно.  
  
 Подробные сведения о параметрах, необходимых для функции SEMANTICKEYPHRASETABLE, и о таблице возвращаемых ей результатов см. в разделе [semantickeyphrasetable (Transact-SQL)](../../relational-databases/system-functions/semantickeyphrasetable-transact-sql.md).  
  
> [!IMPORTANT]  
>  Для целевых столбцов должно быть включено полнотекстовое и семантическое индексирование.  
  
###  <a name="example-1-find-the-top-key-phrases-in-a-specific-document"></a><a name="HowToTopPhrases"></a> Пример 1. Поиск наиболее важных ключевых фраз в определенном документе  
 В следующем примере извлекаются 10 первых ключевых фраз из документа, указанного в переменной @DocumentId в столбце Document таблицы Production.Document в тестовой базе данных AdventureWorks. Переменная @DocumentId представляет значение из ключевого столбца полнотекстового индекса.  
  
```sql  
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
  
###  <a name="example-2-find-the-top-documents-that-contain-a-specific-key-phrase"></a><a name="HowToTopDocuments"></a> Пример 2. Поиск документов, содержащих определенную ключевую фразу  
 В следующем примере извлекаются 25 первых документов, содержащих ключевую фразу Bracket в столбце Document таблицы Production.Document примера базы данных AdventureWorks.  
  
```sql  
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
  
  
