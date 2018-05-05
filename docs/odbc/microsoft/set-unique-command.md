---
title: Команда УНИКАЛЬНЫЙ НАБОР | Документы Microsoft
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
- SET UNIQUE command [ODBC]
ms.assetid: 1f69e31e-4599-47cc-ac89-b86fba8703c5
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: dbdb92c553b5d4ff3eae3bf0f0c39fa834bcd913
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="set-unique-command"></a>УНИКАЛЬНЫЙ команды SET
Указывает, хранятся ли записи с повторяющимися значениями ключей в файле индекса.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
SET UNIQUE ON | OFF  
```  
  
## <a name="arguments"></a>Аргументы  
 ON  
 Указывает, не включены все записи со значением ключа индекса повторяющиеся в файле индекса. В файле индекса включается первой записи с исходное значение ключа индекса.  
  
 OFF  
 (По умолчанию). Указывает, что записи с повторяющимися значениями ключей будут включены в файл индекса.  
  
## <a name="remarks"></a>Замечания  
 Индексный файл сохраняет его ЗАДАТЬ УНИКАЛЬНЫЙ параметр выполните повторную ИНДЕКСАЦИЮ. Дополнительные сведения см. в разделе [ИНДЕКСА](../../odbc/microsoft/index-command.md).
