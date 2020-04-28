---
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
ms.openlocfilehash: c6aa512ff789fcbd00f45f84fb194d4ab3f5da07
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "81280974"
---
# <a name="create-index-statement"></a>Инструкция CREATE INDEX
Синтаксис инструкции CREATE INDEX:  
  
 CREATE [UNIQUE] *индекс index-Name* для *Table-name* (*столбец-Идентификатор* [ASC] [desc] [, *столбец-Идентификатор* [ASC] [desc]...]) С \<помощью *списка параметров индекса*>  
  
 \<> *списка параметров индекса* может быть: Primary &#124; запретить NULL &#124; пропускать null  
  
 Только драйвер Microsoft Access использует параметры "запретить NULL" и "игнорировать пустые индексы". Драйверы dBASE и Paradox принимают синтаксис, но игнорируют присутствие любого из этих параметров.  
  
 При использовании драйвера Paradox инструкция CREATE INDEX создает файлы первичного ключа Paradox и вторичные файлы.  
  
 Эта инструкция не поддерживается драйверами Microsoft Excel и Text.
