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
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- DELETE statement limitations [ODBC]
- ODBC SQL grammar, DELETE statement limitations
ms.assetid: 084761fe-e65b-4f38-ba4f-69884b2a7700
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 767008325089473195f4ceb6f71c54d4e1890090
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/20/2017
---
# <a name="delete-statement-limitations"></a>Удаление ограничения на инструкции
Инструкции DELETE не поддерживается для драйвера Microsoft Excel или текст. Обратите внимание, что поддерживаются инструкции INSERT в текстовый драйвер.  
  
 Драйвер dBASE не поддерживает упаковки таблицу для удаления значений «удалено».  
  
 Для драйвера Paradox удаление строки из таблицы таблица должна иметь уникальный индекс (Paradox первичный ключ).
