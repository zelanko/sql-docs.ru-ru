---
title: Ограничения инструкции DROP TABLE | Документация Майкрософт
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: c296108b9ab26a6361d12ad71a1f21b21d5bea1e
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "81303405"
---
# <a name="drop-table-statement-limitations"></a>Ограничения инструкции DROP TABLE
При использовании драйвера Microsoft Excel 5,0, 7,0 или 97 инструкция DROP TABLE очищает лист, но не удаляет имя листа. Так как имя листа по-прежнему существует в книге, нельзя создать другой лист с таким же именем.
