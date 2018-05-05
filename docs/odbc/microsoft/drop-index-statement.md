---
title: Инструкция DROP INDEX | Документы Microsoft
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
ms.topic: conceptual
helpviewer_keywords:
- DROP INDEX [ODBC]
- SQL grammar [ODBC], DROP INDEX
ms.assetid: cd0ff767-9254-413b-bd1a-bed26c6774f5
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: aef4e44ff71a000345dff42a01d5e5e75a13bdd1
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="drop-index-statement"></a>Инструкция DROP INDEX
Когда используется драйвер Microsoft Access, dBASE или Paradox, синтаксис инструкции DROP INDEX является «DROP INDEX on b» где «» — имя индекса, а «b» — имя таблицы (DROP INDEX не *имя индекса*).  
  
 При использовании драйвера Paradox инструкции DROP INDEX удаляет файлы Paradox вторичного индекса.  
  
 Инструкции DROP INDEX не поддерживается для драйверов Microsoft Excel или текст.
