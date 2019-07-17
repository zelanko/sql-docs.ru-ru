---
title: Изменения в поведении | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- backward compatibility [ODBC], behavioral changes
- behavioral changes [ODBC]
- compatibility [ODBC], behavioral changes
ms.assetid: a17ae701-6ab6-4eaf-9e46-d3b9cd0a3a67
author: MightyPen
ms.author: genemi
ms.openlocfilehash: fc9f8dcc3782204c8bf1c9add1200e451edcf127
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68103867"
---
# <a name="behavioral-changes"></a>Изменения в поведении
Изменения поведения являются эти изменения, для которого *синтаксис* интерфейса остается тем же, но *семантику* были изменены. Чтобы эти изменения, функциональные возможности, используемые в ODBC 2. *x* ведет себя иначе, чем те же функциональные возможности в ODBC 3. *x*.  
  
 Является ли приложение демонстрирует ODBC 2. *x* поведение или ODBC 3. *x* поведение определяется атрибут SQL_ATTR_ODBC_VERSION среды. Это 32-разрядное значение присваивается SQL_OV_ODBC2 которых ODBC 2. *x* поведение и значение SQL_OV_ODBC3 которых ODBC 3. *x* поведение.  
  
 Атрибут среды SQL_ATTR_ODBC_VERSION установлен с помощью вызова **SQLSetEnvAttr**. После приложение вызывает **SQLAllocHandle** выделить дескриптор среды, он должен вызвать**SQLSetEnvAttr** немедленно, чтобы задать поведение, он демонстрирует. (Таким образом, нет в новой среде состояние для описания дескриптора среды в выделенные, но versionless, состояние.) Дополнительные сведения см. в разделе [приложении б: Таблицы перехода состояния ODBC](../../../odbc/reference/appendixes/appendix-b-odbc-state-transition-tables.md).  
  
 Приложение утверждается, какое именно поведение он демонстрирует с атрибуту окружения SQL_ATTR_ODBC_VERSION, однако атрибут не оказывает влияния на подключение к приложению с помощью ODBC 2. *x* или ODBC 3. *x* драйвера. ODBC 3. *x* приложение может подключаться к либо ODBC 2. *x* или 3. *x* драйвера, независимо от значения атрибута среды.  
  
 ODBC 3. *x* приложения никогда не должны вызывать метод **SQLAllocEnv**. В результате, если диспетчер драйверов получает вызов **SQLAllocEnv**, он распознает приложение как ODBC 2. *x* приложения.  
  
 Атрибут SQL_ATTR_ODBC_VERSION влияет на три различные аспекты ODBC 3. *x* поведение драйвера:  
  
-   атрибуты SQLSTATE  
  
-   Типы данных для дат, времени и метки времени  
  
-   *CatalogName* аргумента в **SQLTables** принимает шаблонов поиска в ODBC 3. *x*, но не в ODBC 2. *x*  
  
 Параметр атрибута среды SQL_ATTR_ODBC_VERSION не влияет на **SQLSetParam** или **SQLBindParam**. **SQLColAttribute** не зависит от этот бит. Несмотря на то что **SQLColAttribute** возвращает атрибуты, на которые влияет по версии ODBC (тип date, точность, масштаб и длина), предполагаемое поведение определяется по значению *FieldIdentifier*аргумент. Когда *FieldIdentifier* равен SQL_DESC_TYPE, **SQLColAttribute** возвращает ODBC 3. *x* коды для date, time и timestamp; при *FieldIdentifier* равен SQL_COLUMN_TYPE, **SQLColAttribute** возвращает ODBC 2. *x* коды для date, time и timestamp.  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Сопоставления SQLSTATE](../../../odbc/reference/develop-app/sqlstate-mappings.md)  
  
-   [Изменения в типе данных Datetime](../../../odbc/reference/develop-app/datetime-data-type-changes.md)
