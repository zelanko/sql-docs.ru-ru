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
ms.openlocfilehash: ad15ad436b0f34f00acbd75e371e998183f22d2f
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68081911"
---
# <a name="create-index-statement"></a>Инструкция CREATE INDEX
Используется следующий синтаксис инструкции CREATE INDEX:  
  
 Создание ИНДЕКСА [UNIQUE] *имя индекса* ON *имя таблицы* (*идентификатор столбца* [ASC] [DESC] [, *идентификатор столбца* [ASC][DESC]...]) С помощью \< *список параметров индекса*>  
  
 где \< *список параметров индекса*> может быть: ОСНОВНОЙ &#124; DISALLOW NULL &#124; IGNORE NULL  
  
 Только драйвером Microsoft Access использует параметры индекса запретить NULL и ИГНОРИРОВАТЬ NULL. DBASE и драйверов для Paradox принимать синтаксис, но не учитывать наличие любого из этих вариантов.  
  
 Если используется драйвер для Paradox, инструкции CREATE INDEX создает первичные файлы ключа для Paradox и вторичных файлов.  
  
 Эта инструкция не поддерживается Microsoft Excel или текстовый драйверы.
