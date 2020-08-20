---
description: Функции каталога полнотекстового и семантического поиска (Transact-SQL)
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
ms.openlocfilehash: deb790da4e4e263318717c3ee81cc8ee8d467ae6
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88474657"
---
# <a name="full-text-search-and-semantic-search-functions-transact-sql"></a>Функции каталога полнотекстового и семантического поиска (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  В этом разделе описаны системные функции, связанные с полнотекстовым и семантическим поиском.  
  
## <a name="full-text-search-functions"></a>Функции полнотекстового поиска  
 [CONTAINSTABLE (Transact-SQL)](../../relational-databases/system-functions/containstable-transact-sql.md)  
 Возвращает пустую таблицу или таблицу из одной или нескольких строк. Столбцы этой таблицы содержат символьные данные, точно или нечетко (менее точно) соответствующие отдельным словам и фразам, расстоянию между словами или взвешенным совпадениям.  
  
 [FREETEXTTABLE (Transact-SQL)](../../relational-databases/system-functions/freetexttable-transact-sql.md)  
 Возвращает таблицу из нуля, одну или несколько строк для столбцов, содержащих значения, которые соответствуют значению, а не только точное слово текста в заданном *freetext_string*.  
  
## <a name="semantic-search-functions"></a>Функции семантического поиска  
 [semantickeyphrasetable (Transact-SQL)](../../relational-databases/system-functions/semantickeyphrasetable-transact-sql.md)  
 Возвращает таблицу с нулем, одной или несколькими строками для ключевых фраз, связанных со столбцами в указанной таблице.  
  
 [semanticsimilaritydetailstable (Transact-SQL)](../../relational-databases/system-functions/semanticsimilaritydetailstable-transact-sql.md)  
 Возвращает таблицу из 0, одной или более строк с ключевыми фразами, общими для двух документов (исходного документа и сопоставленного документа), содержимое которых семантически сходно.  
  
 [semanticsimilaritytable (Transact-SQL)](../../relational-databases/system-functions/semanticsimilaritytable-transact-sql.md)  
 Возвращает таблицу из нуля, одной или более строк для столбцов, содержимое которых семантически сходно с указанным документом.  
  
  
