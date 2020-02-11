---
title: Изменения поведения | Документация Майкрософт
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
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68103867"
---
# <a name="behavioral-changes"></a>Изменения в поведении
Изменения поведения — это изменения, для которых *синтаксис* интерфейса остается прежним, но *семантика* изменилась. Для этих изменений функции, используемые в ODBC 2. *x* ведет себя иначе, чем те же функциональные возможности ODBC 3. *x*.  
  
 Относится ли приложение к ODBC 2. поведение *x* или ODBC 3. поведение *x* определяется атрибутом среды SQL_ATTR_ODBC_VERSION. Это 32-разрядное значение установлено в SQL_OV_ODBC2 для ODBC 2. поведение *x* и SQL_OV_ODBC3 для работы с ODBC 3. поведение по *оси x* .  
  
 Атрибут среды SQL_ATTR_ODBC_VERSION задается вызовом **SQLSetEnvAttr**. После того как приложение вызывает **функцию SQLAllocHandle** для выделения обработчика среды, оно должно вызывать**SQLSetEnvAttr** немедленно, чтобы задать поведение, которое он называет. (В результате существует новое состояние среды для описания обработчика среды в выделенном состоянии, но без поддержки версий.) Дополнительные сведения см. в [приложении б: таблицы переходов состояния ODBC](../../../odbc/reference/appendixes/appendix-b-odbc-state-transition-tables.md).  
  
 В приложении указывается поведение, которое он содержит для атрибута среды SQL_ATTR_ODBC_VERSION, но атрибут не влияет на соединение приложения с ODBC 2. *x* или ODBC 3. драйвер *x* . ODBC 3. Приложение *x* может подключаться к ODBC 2. *x* или 3. *x* , независимо от значения атрибута Environment.  
  
 ODBC 3. приложения *x* никогда не должны вызывать **SQLAllocEnv**. В результате, если диспетчер драйверов получает вызов **SQLAllocEnv**, он распознает приложение как ODBC 2. Приложение *x* .  
  
 Атрибут SQL_ATTR_ODBC_VERSION влияет на три различных аспекта ODBC 3. поведение драйвера *x* :  
  
-   атрибуты SQLSTATE  
  
-   Типы данных для даты, времени и метки времени  
  
-   Аргумент *CatalogName* в **SQLTables** принимает шаблоны поиска в ODBC 3. *x*, но не в ODBC 2. *x*  
  
 Значение атрибута среды SQL_ATTR_ODBC_VERSION не влияет на **SQLSetParam** или **склбиндпарам**. На **SQLColAttribute** также не влияет этот бит. Несмотря на то, что **SQLColAttribute** возвращает атрибуты, затрагиваемые версией ODBC (тип даты, точность, масштаб и длина), предполагаемое поведение определяется значением аргумента *фиелдидентифиер* . Если *фиелдидентифиер* равен SQL_DESC_TYPE, **SQLColAttribute** возвращает ODBC 3. коды *x* для даты, времени и метки времени; Если *фиелдидентифиер* равен SQL_COLUMN_TYPE, **SQLColAttribute** возвращает ODBC 2. коды *x* для даты, времени и метки времени.  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Сопоставления SQLSTATE](../../../odbc/reference/develop-app/sqlstate-mappings.md)  
  
-   [Изменения в типе данных Datetime](../../../odbc/reference/develop-app/datetime-data-type-changes.md)
