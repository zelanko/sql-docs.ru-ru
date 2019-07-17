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
ms.openlocfilehash: 6e798a9c7fa3365082a2e6dab562596d56649ec4
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68088025"
---
# <a name="using-synonyms-with-stored-procedures"></a>Использование синонимов с хранимыми процедурами
> [!IMPORTANT]  
>  Этот компонент будет удален в будущих версиях Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Вместо этого используйте драйвер ODBC, предоставляемого корпорацией Oracle.  
  
 Драйвер Microsoft ODBC для Oracle версии 2.0 и 2.5 не поддерживают синонимы при Oracle вызова хранимых процедур. Синонимы работать некорректно при использовании с другими объектами базы данных Oracle, такие как таблицы.
