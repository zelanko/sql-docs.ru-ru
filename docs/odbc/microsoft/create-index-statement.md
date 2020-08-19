---
description: Инструкция CREATE INDEX
title: CREATE INDEX, инструкция | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- CREATE INDEX [ODBC]
- SQL grammar [ODBC], create index
ms.assetid: 69438247-eef3-44c5-bef2-acef4e146f41
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 7a3f5a13624cdb137e8c86cf2c27044c6705298f
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88483637"
---
# <a name="create-index-statement"></a>Инструкция CREATE INDEX
Синтаксис инструкции CREATE INDEX:  
  
 CREATE [UNIQUE] *индекс index-Name* для *Table-name* (*столбец-Идентификатор* [ASC] [desc] [, *столбец-Идентификатор* [ASC] [desc]...]) УЧЕТ \<*index option list*>  
  
 где \<*index option list*> может быть: PRIMARY &#124; запретить null &#124; Ignore null  
  
 Только драйвер Microsoft Access использует параметры "запретить NULL" и "игнорировать пустые индексы". Драйверы dBASE и Paradox принимают синтаксис, но игнорируют присутствие любого из этих параметров.  
  
 При использовании драйвера Paradox инструкция CREATE INDEX создает файлы первичного ключа Paradox и вторичные файлы.  
  
 Эта инструкция не поддерживается драйверами Microsoft Excel и Text.
