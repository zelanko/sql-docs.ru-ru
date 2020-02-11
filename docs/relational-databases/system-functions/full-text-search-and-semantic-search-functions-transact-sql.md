---
title: Функции полнотекстового поиска и семантического поиска (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- semantic search [SQL Server], system functions
ms.assetid: a61a3694-7604-4583-962e-fc30f771c6fa
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 58bf5650a5ab06783ad0c889bc3286184a7d73ed
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68042752"
---
# <a name="full-text-search-and-semantic-search-functions-transact-sql"></a>Функции каталога полнотекстового и семантического поиска (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  В этом разделе описаны системные функции, связанные с полнотекстовым и семантическим поиском.  
  
## <a name="full-text-search-functions"></a>Функции полнотекстового поиска  
 [Функция CONTAINSTABLE &#40;Transact-SQL&#41;](../../relational-databases/system-functions/containstable-transact-sql.md)  
 Возвращает пустую таблицу или таблицу из одной или нескольких строк. Столбцы этой таблицы содержат символьные данные, точно или нечетко (менее точно) соответствующие отдельным словам и фразам, расстоянию между словами или взвешенным совпадениям.  
  
 [&#41;а FREETEXTTABLE &#40;Transact-SQL](../../relational-databases/system-functions/freetexttable-transact-sql.md)  
 Возвращает таблицу из нуля, одну или несколько строк для столбцов, содержащих значения, которые соответствуют значению, а не только точное слово текста в заданном *freetext_string*.  
  
## <a name="semantic-search-functions"></a>Функции семантического поиска  
 [SEMANTICKEYPHRASETABLE &#40;Transact-SQL&#41;](../../relational-databases/system-functions/semantickeyphrasetable-transact-sql.md)  
 Возвращает таблицу с нулем, одной или несколькими строками для ключевых фраз, связанных со столбцами в указанной таблице.  
  
 [SEMANTICSIMILARITYDETAILSTABLE &#40;Transact-SQL&#41;](../../relational-databases/system-functions/semanticsimilaritydetailstable-transact-sql.md)  
 Возвращает таблицу из 0, одной или более строк с ключевыми фразами, общими для двух документов (исходного документа и сопоставленного документа), содержимое которых семантически сходно.  
  
 [SEMANTICSIMILARITYTABLE &#40;Transact-SQL&#41;](../../relational-databases/system-functions/semanticsimilaritytable-transact-sql.md)  
 Возвращает таблицу из нуля, одной или более строк для столбцов, содержимое которых семантически сходно с указанным документом.  
  
  
