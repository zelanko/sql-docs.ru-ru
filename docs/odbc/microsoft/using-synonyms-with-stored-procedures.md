---
title: Использование синонимов с хранимыми процедурами | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- stored procedures [ODBC], ODBC driver for Oracle
- ODBC driver for Oracle [ODBC], stored procedures
ms.assetid: 8620b039-a086-4534-8710-cc8b1787dc80
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: cf56bcc674299fd576529929da10763c26a74ed4
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47711462"
---
# <a name="using-synonyms-with-stored-procedures"></a>Использование синонимов с хранимыми процедурами
> [!IMPORTANT]  
>  Этот компонент будет удален в будущих версиях Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Вместо этого используйте драйвер ODBC, предоставляемого корпорацией Oracle.  
  
 Драйвер Microsoft ODBC для Oracle версии 2.0 и 2.5 не поддерживают синонимы при Oracle вызова хранимых процедур. Синонимы работать некорректно при использовании с другими объектами базы данных Oracle, такие как таблицы.
