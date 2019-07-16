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
ms.openlocfilehash: 49ee96941c69da962e7c000c33d6eb14f66d4dab
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68031147"
---
# <a name="drop-table-statement-limitations"></a>Ограничения инструкции DROP TABLE
При использовании драйвера Microsoft Excel 5.0, 7.0 или 97 инструкцию DROP TABLE удаляет рабочего листа, но не удаляет имя листа. Так как имя листа по-прежнему существует в книге, невозможно создать другой лист с тем же именем.
