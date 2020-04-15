---
title: Поведенческие изменения Документы Майкрософт
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 3e4a433531d90eb0f89d9a5e446464b13fd02526
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81283444"
---
# <a name="behavioral-changes"></a>Изменения в поведении
Поведенческие изменения — это те изменения, для которых *синтаксис* интерфейса остается неизменным, но *семантика* изменилась. Для этих изменений функциональность используется в ODBC 2. *x* ведет себя иначе, чем та же функция в ODBC 3. *x*.  
  
 Является ли приложение экспонатов ODBC 2. *x* поведение или ODBC 3. поведение *x* определяется атрибутом среды SQL_ATTR_ODBC_VERSION. Это 32-битное значение установлено, чтобы SQL_OV_ODBC2, чтобы показать ODBC 2. *x* поведение, и SQL_OV_ODBC3, чтобы показать ODBC 3. *x* поведение.  
  
 Атрибут SQL_ATTR_ODBC_VERSION среды устанавливается вызовом в **S'LSetEnvAttr.** После того, как приложение вызывает **s'LAllocHandle** для выделения ручки среды, оно должно немедленно вызвать**S'LSetEnvAttr,** чтобы установить поведение, которое оно проявляет. (В результате возникает новое состояние среды для описания обработки среды в выделенном, но безверсионном состоянии.) Для получения дополнительной информации [см.](../../../odbc/reference/appendixes/appendix-b-odbc-state-transition-tables.md)  
  
 Приложение указывает, какое поведение оно проявляет с атрибутом среды SQL_ATTR_ODBC_VERSION, но атрибут не влияет на связь приложения с ODBC 2. *x* или ODBC 3. *x* драйвер. ODBC 3. *приложение x* может подключаться к ODBC 2. *x* или 3. *x* драйвер, независимо от того, что параметр атрибута среды.  
  
 ODBC 3. *x* приложения никогда не должны вызывать **S'LAllocEnv**. В результате, если менеджер драйвера получает звонок в **S'LAllocEnv,** он распознает приложение как ODBC 2. *x* приложение.  
  
 Атрибут SQL_ATTR_ODBC_VERSION влияет на три различных аспекта ODBC 3. поведение водителя *x:*  
  
-   атрибуты SQLSTATE  
  
-   Типы данных для даты, времени и метки времени  
  
-   Аргумент *CatalogName* в **S'LTables** принимает шаблоны поиска в ODBC 3. *x*, но не в ODBC 2. *x*  
  
 Настройка атрибута среды SQL_ATTR_ODBC_VERSION не влияет на **S'LSetParam** или **S'LBindParam.** Этот бит также не влияет на **s'LColAttribute.** Несмотря на то, что **s'LColAttribute** возвращает атрибуты, на которые влияет версия ODBC (тип даты, точность, масштаб и длина), предполагаемое поведение определяется значением аргумента *FieldIdentifier.* Когда *FieldIdentifier* равен SQL_DESC_TYPE, **S'LColAttribute** возвращает ODBC 3. *x* коды для даты, времени и метки времени; когда *FieldIdentifier* равен SQL_COLUMN_TYPE, **S'LColAttribute** возвращает ODBC 2. *x* коды для даты, времени и метки времени.  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Сопоставления SQLSTATE](../../../odbc/reference/develop-app/sqlstate-mappings.md)  
  
-   [Изменения в типе данных Datetime](../../../odbc/reference/develop-app/datetime-data-type-changes.md)
