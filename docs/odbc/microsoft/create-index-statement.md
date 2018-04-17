---
title: Индекс инструкция CREATE | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- CREATE INDEX [ODBC]
- SQL grammar [ODBC], create index
ms.assetid: 69438247-eef3-44c5-bef2-acef4e146f41
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 61d1532e457748b432e5aa14a55e9e68b4486c9c
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="create-index-statement"></a>Создание инструкции ИНДЕКСА
Используется синтаксис инструкции CREATE INDEX.  
  
 CREATE [UNIQUE] индекс *имя индекса* ON *имя таблицы* (*идентификатор столбца* [ASC] [DESC] [, *идентификатор столбца* [ASC][DESC]...]) С \< *список параметров индекса*>  
  
 где \< *список параметров индекса*> может быть: ОСНОВНОЙ &#124; DISALLOW NULL &#124; IGNORE NULL  
  
 Только драйвером Microsoft Access использует параметры индекса DISALLOW NULL и ИГНОРИРОВАТЬ NULL. DBASE и драйверы Paradox принимает синтаксис, но не учитывать наличие любого из этих вариантов.  
  
 При использовании драйвера Paradox инструкцию CREATE INDEX создает Paradox файлы первичного ключа и вторичных файлов.  
  
 Эта инструкция не поддерживается Microsoft Excel или текстовый драйвер.
