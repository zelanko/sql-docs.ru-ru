---
title: Ограничения инструкции DELETE | Документы Microsoft
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
- DELETE statement limitations [ODBC]
- ODBC SQL grammar, DELETE statement limitations
ms.assetid: 084761fe-e65b-4f38-ba4f-69884b2a7700
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: caa4855c83815c8876c4674bf01de3f9c4bd4231
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
ms.locfileid: "32898859"
---
# <a name="delete-statement-limitations"></a>Удаление ограничения на инструкции
Инструкции DELETE не поддерживается для драйвера Microsoft Excel или текст. Обратите внимание, что поддерживаются инструкции INSERT в текстовый драйвер.  
  
 Драйвер dBASE не поддерживает упаковки таблицу для удаления значений «удалено».  
  
 Для драйвера Paradox удаление строки из таблицы таблица должна иметь уникальный индекс (Paradox первичный ключ).
