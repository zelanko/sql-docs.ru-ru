---
title: Инструкция CREATE INDEX | Документация Майкрософт
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
manager: craigg
ms.openlocfilehash: 93ddc3881796aee3194ec5268afc68ecbab1a487
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "63233007"
---
# <a name="create-index-statement"></a>Инструкция CREATE INDEX
Используется следующий синтаксис инструкции CREATE INDEX:  
  
 Создание ИНДЕКСА [UNIQUE] *имя индекса* ON *имя таблицы* (*идентификатор столбца* [ASC] [DESC] [, *идентификатор столбца* [ASC][DESC]...]) С помощью \< *список параметров индекса*>  
  
 где \< *список параметров индекса*> может быть: ОСНОВНОЙ &AMP;#124; DISALLOW NULL &AMP;#124; IGNORE NULL  
  
 Только драйвером Microsoft Access использует параметры индекса запретить NULL и ИГНОРИРОВАТЬ NULL. DBASE и драйверов для Paradox принимать синтаксис, но не учитывать наличие любого из этих вариантов.  
  
 Если используется драйвер для Paradox, инструкции CREATE INDEX создает первичные файлы ключа для Paradox и вторичных файлов.  
  
 Эта инструкция не поддерживается Microsoft Excel или текстовый драйверы.
