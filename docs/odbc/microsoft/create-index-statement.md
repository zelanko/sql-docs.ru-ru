---
title: Индекс инструкция CREATE | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- CREATE INDEX [ODBC]
- SQL grammar [ODBC], create index
ms.assetid: 69438247-eef3-44c5-bef2-acef4e146f41
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 86d4cf1bb047cd475b86b9a58c37f3268c07c91d
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
ms.locfileid: "32900021"
---
# <a name="create-index-statement"></a>Создание инструкции ИНДЕКСА
Используется синтаксис инструкции CREATE INDEX.  
  
 CREATE [UNIQUE] индекс *имя индекса* ON *имя таблицы* (*идентификатор столбца* [ASC] [DESC] [, *идентификатор столбца* [ASC][DESC]...]) С \< *список параметров индекса*>  
  
 где \< *список параметров индекса*> может быть: ОСНОВНОЙ &#124; DISALLOW NULL &#124; IGNORE NULL  
  
 Только драйвером Microsoft Access использует параметры индекса DISALLOW NULL и ИГНОРИРОВАТЬ NULL. DBASE и драйверы Paradox принимает синтаксис, но не учитывать наличие любого из этих вариантов.  
  
 При использовании драйвера Paradox инструкцию CREATE INDEX создает Paradox файлы первичного ключа и вторичных файлов.  
  
 Эта инструкция не поддерживается Microsoft Excel или текстовый драйвер.
