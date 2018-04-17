---
title: Ограничения инструкции DROP таблицы | Документы Microsoft
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
- ODBC SQL grammar, DROP TABLE statement limitations
- DROP TABLE statement limitations [ODBC]
ms.assetid: 0a1c80f5-c9f2-4655-9bfd-0131b2f015a9
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: ae6cfb8306c2422585dbb8775e4863108004a5a7
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="drop-table-statement-limitations"></a>Удалите оператор ограничения таблицы
При использовании драйвера Microsoft Excel 5.0, 7.0 или 97 инструкцию DROP TABLE удаляет листа, но не удаляет имя листа. Так как имя листа по-прежнему существуют в книге, невозможно создать другой лист с тем же именем.
