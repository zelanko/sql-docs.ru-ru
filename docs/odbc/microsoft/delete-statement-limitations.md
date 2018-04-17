---
title: Ограничения инструкции DELETE | Документы Microsoft
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
- DELETE statement limitations [ODBC]
- ODBC SQL grammar, DELETE statement limitations
ms.assetid: 084761fe-e65b-4f38-ba4f-69884b2a7700
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 45386d8278e968b55fba5881dfe9b914bc23f454
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="delete-statement-limitations"></a>Удаление ограничения на инструкции
Инструкции DELETE не поддерживается для драйвера Microsoft Excel или текст. Обратите внимание, что поддерживаются инструкции INSERT в текстовый драйвер.  
  
 Драйвер dBASE не поддерживает упаковки таблицу для удаления значений «удалено».  
  
 Для драйвера Paradox удаление строки из таблицы таблица должна иметь уникальный индекс (Paradox первичный ключ).
