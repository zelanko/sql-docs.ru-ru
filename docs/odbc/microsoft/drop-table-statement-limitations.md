---
title: Ограничения инструкции DROP таблицы | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC SQL grammar, DROP TABLE statement limitations
- DROP TABLE statement limitations [ODBC]
ms.assetid: 0a1c80f5-c9f2-4655-9bfd-0131b2f015a9
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 4a24a22a5e666421136780f3614db4df2233bc82
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "63128019"
---
# <a name="drop-table-statement-limitations"></a>Ограничения инструкции DROP TABLE
При использовании драйвера Microsoft Excel 5.0, 7.0 или 97 инструкцию DROP TABLE удаляет рабочего листа, но не удаляет имя листа. Так как имя листа по-прежнему существует в книге, невозможно создать другой лист с тем же именем.
