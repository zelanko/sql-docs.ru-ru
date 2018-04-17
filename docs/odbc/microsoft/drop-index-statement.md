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
ms.topic: article
helpviewer_keywords:
- DROP INDEX [ODBC]
- SQL grammar [ODBC], DROP INDEX
ms.assetid: cd0ff767-9254-413b-bd1a-bed26c6774f5
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 806b1ec9338f877bc573a8c0c2930498c898037e
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="drop-index-statement"></a>Инструкция DROP INDEX
Когда используется драйвер Microsoft Access, dBASE или Paradox, синтаксис инструкции DROP INDEX является «DROP INDEX on b» где «» — имя индекса, а «b» — имя таблицы (DROP INDEX не *имя индекса*).  
  
 При использовании драйвера Paradox инструкции DROP INDEX удаляет файлы Paradox вторичного индекса.  
  
 Инструкции DROP INDEX не поддерживается для драйверов Microsoft Excel или текст.
