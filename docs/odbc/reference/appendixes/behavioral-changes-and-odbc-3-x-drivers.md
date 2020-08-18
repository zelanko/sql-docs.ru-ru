---
description: Изменения в поведении и драйверы ODBC 3.x
title: Изменения поведения и драйверы ODBC 3. x | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- sql_attr_odbc_version [ODBC]
- backward compatibility [ODBC], behavioral changes
- compatibility [ODBC], behavioral changes
ms.assetid: 88a503cc-bff7-42d9-83ff-8e232109ed06
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 43f64aa4b627130308ea920918c2de6d98116020
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88411340"
---
# <a name="behavioral-changes-and-odbc-3x-drivers"></a>Изменения в поведении и драйверы ODBC 3.x
Атрибут среды SQL_ATTR_ODBC_VERSION указывает драйверу, требуется ли поведение ODBC *2. x* или поведение ODBC *3. x* . Настройка атрибута среды SQL_ATTR_ODBC_VERSION зависит от приложения. Приложения ODBC *3. x* должны вызывать **SQLSetEnvAttr** для установки этого атрибута после вызова **функцию SQLAllocHandle** для выделения обработчика среды и перед вызовом **функцию SQLAllocHandle** для выделения маркера соединения. Если это не удается сделать, диспетчер драйверов возвращает значение SQLSTATE HY010 (ошибка последовательности функций) при последнем вызове функции **функцию SQLAllocHandle**.  
  
> [!NOTE]  
>  Дополнительные сведения об изменениях поведения и о том, как работает приложение, см. в разделе [изменения поведения](../../../odbc/reference/develop-app/behavioral-changes.md).  
  
 Приложения ODBC *2. x* и приложения ODBC *2. x* , перекомпилированные с помощью файлов заголовков ODBC *3. x* , не вызывают **SQLSetEnvAttr**. Однако они вызывают **SQLAllocEnv** вместо **функцию SQLAllocHandle** для выделения маркера среды. Таким образом, когда приложение вызывает **SQLAllocEnv** в диспетчере драйверов, диспетчер драйверов вызывает **функцию SQLAllocHandle** и **SQLSetEnvAttr** в драйвере. Таким словами, драйверы ODBC *3. x* всегда могут подсчитывать значение этого атрибута.  
  
 Если стандартно совместимое приложение, скомпилированное с флагом ODBC_STD Compile, вызывает **SQLAllocEnv** (что может произойти, поскольку **SQLAllocEnv** не является устаревшим в ISO), вызов сопоставляется с **склаллочандлестд** во время компиляции. Во время выполнения приложение вызывает **склаллочандлестд**. Диспетчер драйверов задает для атрибута среды SQL_ATTR_ODBC_VERSION значение SQL_OV_ODBC3. Вызов **склаллочандлестд** эквивалентен вызову **функцию sqlallochandle** с *параметром handletype* SQL_HANDLE_ENV и вызовом **SQLSetEnvAttr** для установки SQL_ATTR_ODBC_VERSION SQL_OV_ODBC3.  
  
 В некоторых архитектурах драйверов необходимо, чтобы драйвер отображался как драйвер ODBC *2. x* или драйвер ODBC *3. x* в зависимости от соединения. В этом случае драйвер может не быть драйвером, а слоем, который находится между диспетчером драйверов и другим драйвером. Например, он может имитировать драйвер, например ODBC Spy. В другом примере он может действовать в качестве шлюза, например EDA/SQL. Для отображения в виде драйвера ODBC *3. x* такой драйвер должен иметь возможность экспорта **функцию SQLAllocHandle**, который должен быть драйвером ODBC *2. x* , иметь возможность экспортировать **SQLAllocConnect**, **SQLAllocEnv**и **SQLAllocStmt**. При выделении среды, соединения или инструкции диспетчер драйверов проверяет, экспортирует ли этот драйвер **функцию SQLAllocHandle**. Так как драйвер работает, диспетчер драйверов вызывает **функцию SQLAllocHandle** в драйвере. Если драйвер работает с драйвером ODBC *2. x* , драйвер должен соответствующим образом сопоставлять вызов **функцию SQLAllocHandle** с **SQLAllocConnect**, **SQLAllocEnv**или **SQLAllocStmt**. При работе в качестве драйвера ODBC *2. x* также необходимо ничего делать с вызовом **SQLSetEnvAttr** .  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Типы данных даты и времени](../../../odbc/reference/appendixes/datetime-data-types.md)  
  
-   [Обратная совместимость типов данных C](../../../odbc/reference/appendixes/backward-compatibility-of-c-data-types.md)  
  
-   [Закладки фиксированной длины](../../../odbc/reference/appendixes/fixed-length-bookmarks.md)  
  
-   [Поддержка SQLGetInfo](../../../odbc/reference/appendixes/sqlgetinfo-support.md)  
  
-   [Возврат SQL_NO_DATA](../../../odbc/reference/appendixes/returning-sql-no-data.md)  
  
-   [Вызов SQLSetPos для вставки данных](../../../odbc/reference/appendixes/calling-sqlsetpos-to-insert-data.md)  
  
-   [Загрузка по порядковому номеру](../../../odbc/reference/appendixes/loading-by-ordinal.md)
