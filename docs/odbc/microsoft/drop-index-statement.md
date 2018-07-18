---
title: Инструкция DROP INDEX | Документы Microsoft
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
- DROP INDEX [ODBC]
- SQL grammar [ODBC], DROP INDEX
ms.assetid: cd0ff767-9254-413b-bd1a-bed26c6774f5
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 9fe21c9f4f21b4154d7a134da00a93264cf0583a
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
ms.locfileid: "32900250"
---
# <a name="drop-index-statement"></a>Инструкция DROP INDEX
Когда используется драйвер Microsoft Access, dBASE или Paradox, синтаксис инструкции DROP INDEX является «DROP INDEX on b» где «» — имя индекса, а «b» — имя таблицы (DROP INDEX не *имя индекса*).  
  
 При использовании драйвера Paradox инструкции DROP INDEX удаляет файлы Paradox вторичного индекса.  
  
 Инструкции DROP INDEX не поддерживается для драйверов Microsoft Excel или текст.
