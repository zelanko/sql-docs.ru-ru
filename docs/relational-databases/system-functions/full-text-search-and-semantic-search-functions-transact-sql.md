---
title: Компонент Full-Text Search и функции семантического поиска (Transact-SQL) | Документация Майкрософт
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
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 5f2a6364d002200cea1c04b35216dcec6dc0743d
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47780992"
---
# <a name="full-text-search-and-semantic-search-functions-transact-sql"></a>Функции каталога полнотекстового и семантического поиска (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  В этом разделе описаны системные функции, связанные с полнотекстовым и семантическим поиском.  
  
## <a name="full-text-search-functions"></a>Функции полнотекстового поиска  
 [CONTAINSTABLE (Transact-SQL)](../../relational-databases/system-functions/containstable-transact-sql.md)  
 Возвращает пустую таблицу или таблицу из одной или нескольких строк. Столбцы этой таблицы содержат символьные данные, точно или нечетко (менее точно) соответствующие отдельным словам и фразам, расстоянию между словами или взвешенным совпадениям.  
  
 [FREETEXTTABLE (Transact-SQL)](../../relational-databases/system-functions/freetexttable-transact-sql.md)  
 Возвращает таблицу из нуля, одной или нескольких строк. столбцы содержат значения, совпадающие по смыслу, но не дословно, с текстом, указанным в *freetext_string*.  
  
## <a name="semantic-search-functions"></a>Функции семантического поиска  
 [semantickeyphrasetable (Transact-SQL)](../../relational-databases/system-functions/semantickeyphrasetable-transact-sql.md)  
 Возвращает таблицу с нулем, одной или несколькими строками для ключевых фраз, связанных со столбцами в указанной таблице.  
  
 [semanticsimilaritydetailstable (Transact-SQL)](../../relational-databases/system-functions/semanticsimilaritydetailstable-transact-sql.md)  
 Возвращает таблицу из 0, одной или более строк с ключевыми фразами, общими для двух документов (исходного документа и сопоставленного документа), содержимое которых семантически сходно.  
  
 [semanticsimilaritytable (Transact-SQL)](../../relational-databases/system-functions/semanticsimilaritytable-transact-sql.md)  
 Возвращает таблицу из нуля, одной или более строк для столбцов, содержимое которых семантически сходно с указанным документом.  
  
  
