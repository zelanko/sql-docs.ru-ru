---
title: "Индекс инструкция CREATE | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: microsoft
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- CREATE INDEX [ODBC]
- SQL grammar [ODBC], create index
ms.assetid: 69438247-eef3-44c5-bef2-acef4e146f41
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 6737ad2bdde9516291863214d3da5dd6087e3ec2
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/20/2017
---
# <a name="create-index-statement"></a>Создание инструкции ИНДЕКСА
Используется синтаксис инструкции CREATE INDEX.  
  
 CREATE [UNIQUE] индекс *имя индекса* ON *имя таблицы* (*идентификатор столбца* [ASC] [DESC] [, *идентификатор столбца* [ASC][DESC]...]) С \< *список параметров индекса*>  
  
 где \< *список параметров индекса*> может быть: ОСНОВНОЙ &#124; ЗАПРЕТИТЬ NULL &#124; ИГНОРИРОВАТЬ NULL  
  
 Только драйвером Microsoft Access использует параметры индекса DISALLOW NULL и ИГНОРИРОВАТЬ NULL. DBASE и драйверы Paradox принимает синтаксис, но не учитывать наличие любого из этих вариантов.  
  
 При использовании драйвера Paradox инструкцию CREATE INDEX создает Paradox файлы первичного ключа и вторичных файлов.  
  
 Эта инструкция не поддерживается Microsoft Excel или текстовый драйвер.
