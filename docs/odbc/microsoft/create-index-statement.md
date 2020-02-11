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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: ad15ad436b0f34f00acbd75e371e998183f22d2f
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68081911"
---
# <a name="create-index-statement"></a>Инструкция CREATE INDEX
Синтаксис инструкции CREATE INDEX:  
  
 CREATE [UNIQUE] *индекс index-Name* для *Table-name* (*столбец-Идентификатор* [ASC] [desc] [, *столбец-Идентификатор* [ASC] [desc]...]) С \<помощью *списка параметров индекса*>  
  
 \<> *списка параметров индекса* может быть: Primary &#124; запретить NULL &#124; пропускать null  
  
 Только драйвер Microsoft Access использует параметры "запретить NULL" и "игнорировать пустые индексы". Драйверы dBASE и Paradox принимают синтаксис, но игнорируют присутствие любого из этих параметров.  
  
 При использовании драйвера Paradox инструкция CREATE INDEX создает файлы первичного ключа Paradox и вторичные файлы.  
  
 Эта инструкция не поддерживается драйверами Microsoft Excel и Text.
