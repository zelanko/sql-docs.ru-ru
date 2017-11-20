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
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- CREATE INDEX [ODBC]
- SQL grammar [ODBC], create index
ms.assetid: 69438247-eef3-44c5-bef2-acef4e146f41
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 0f6e7525059640e7ffdadd79ec26a62229eabae9
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="create-index-statement"></a>Создание инструкции ИНДЕКСА
Используется синтаксис инструкции CREATE INDEX.  
  
 CREATE [UNIQUE] индекс *имя индекса* ON *имя таблицы* (*идентификатор столбца* [ASC] [DESC] [, *идентификатор столбца* [ASC][DESC]...]) С \< *список параметров индекса*>  
  
 где \< *список параметров индекса*> может быть: ОСНОВНОЙ &#124; ЗАПРЕТИТЬ NULL &#124; ИГНОРИРОВАТЬ NULL  
  
 Только драйвером Microsoft Access использует параметры индекса DISALLOW NULL и ИГНОРИРОВАТЬ NULL. DBASE и драйверы Paradox принимает синтаксис, но не учитывать наличие любого из этих вариантов.  
  
 При использовании драйвера Paradox инструкцию CREATE INDEX создает Paradox файлы первичного ключа и вторичных файлов.  
  
 Эта инструкция не поддерживается Microsoft Excel или текстовый драйвер.

