---
title: "Ограничения инструкции DELETE | Документы Microsoft"
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
- DELETE statement limitations [ODBC]
- ODBC SQL grammar, DELETE statement limitations
ms.assetid: 084761fe-e65b-4f38-ba4f-69884b2a7700
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: d8ffdb2fa548b03ee38c0f817675cb88ab4acf67
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="delete-statement-limitations"></a>Удаление ограничения на инструкции
Инструкции DELETE не поддерживается для драйвера Microsoft Excel или текст. Обратите внимание, что поддерживаются инструкции INSERT в текстовый драйвер.  
  
 Драйвер dBASE не поддерживает упаковки таблицу для удаления значений «удалено».  
  
 Для драйвера Paradox удаление строки из таблицы таблица должна иметь уникальный индекс (Paradox первичный ключ).

