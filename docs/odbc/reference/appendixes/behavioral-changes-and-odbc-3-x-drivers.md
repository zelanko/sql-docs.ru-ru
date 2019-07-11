---
title: Изменения в поведении и драйверы ODBC 3.x | Документация Майкрософт
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 18dd126363d39f4352298cf672922c6113482764
ms.sourcegitcommit: 56b963446965f3a4bb0fa1446f49578dbff382e0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/11/2019
ms.locfileid: "67793234"
---
# <a name="behavioral-changes-and-odbc-3x-drivers"></a>Изменения в поведении и драйверы ODBC 3.x
Атрибут среды SQL_ATTR_ODBC_VERSION Указывает драйверу, должен ли он может представлять ODBC *2.x* поведение или ODBC *3.x* поведение. Как задается атрибут SQL_ATTR_ODBC_VERSION среды зависит от приложения. ODBC *3.x* приложений необходимо вызвать **SQLSetEnvAttr** для установки этого атрибута, после они вызывают **SQLAllocHandle** выделить дескриптор среды и до вызова  **SQLAllocHandle** выделить дескриптор соединения. Если они забывают про это, диспетчер драйверов возвращает параметром SQLSTATE HY010 (функционировать ошибка последовательности) при последнем вызове **SQLAllocHandle**.  
  
> [!NOTE]  
>  Дополнительные сведения о изменения в поведении и как работает приложение, см. в разделе [изменения в поведении](../../../odbc/reference/develop-app/behavioral-changes.md).  
  
 ODBC *2.x* приложений и ODBC *2.x* приложений, перекомпилируются ODBC *3.x* файлы заголовков не следует вызывать **SQLSetEnvAttr**. Тем не менее, они вызывают **SQLAllocEnv** вместо **SQLAllocHandle** выделить дескриптор среды. Таким образом, когда приложение вызывает **SQLAllocEnv** диспетчера драйверов, диспетчер драйверов вызывает **SQLAllocHandle** и **SQLSetEnvAttr** в драйвере. Таким образом, ODBC *3.x* драйверы всегда могли полагаться на этот атрибут.  
  
 Если соответствующих стандартам приложений компилируется с флагом компиляции ODBC_STD вызовы **SQLAllocEnv** (которой может возникать **SQLAllocEnv** не является устаревшей в ISO), вызов сопоставлен с  **SQLAllocHandleStd** во время компиляции. Во время выполнения, приложение вызывает **SQLAllocHandleStd**. Диспетчер драйверов задает атрибуту окружения SQL_ATTR_ODBC_VERSION значение sql_ov_odbc3. Вызов **SQLAllocHandleStd** эквивалентен вызов **SQLAllocHandle** с *HandleType* SQL_HANDLE_ENV и вызов **SQLSetEnvAttr** присвоено значение SQL_ATTR_ODBC_VERSION значение SQL_OV_ODBC3.  
  
 В определенных архитектуры драйверов есть потребность в виде либо ODBC драйвер *2.x* или драйвер ODBC *3.x* драйвера, в зависимости от подключения. Драйвер в этом случае может оказаться фактически драйвер, но это слой, который находится между диспетчера драйверов и драйверов. Например он имитируют драйвером, такие как ODBC Spy. В другом примере он может выступать в качестве шлюза, например EDA/SQL. Для отображения в виде ODBC *3.x* драйвера, такой драйвер должен иметь возможность экспортировать **SQLAllocHandle**и отображаются в виде ODBC *2.x* драйвер, должен иметь возможность экспортировать  **SQLAllocConnect**, **SQLAllocEnv**, и **SQLAllocStmt**. Если оператор среды, подключения или для распределения, диспетчер драйверов проверяет, экспортирует этот драйвер **SQLAllocHandle**. Так как драйвер выполняет, диспетчер драйверов вызывает **SQLAllocHandle** в драйвере. Если драйвер работает с ODBC *2.x* драйвера, драйвер необходимо сопоставить вызов **SQLAllocHandle** для **SQLAllocConnect**, **SQLAllocEnv**, или **SQLAllocStmt**, соответствующим образом. Он должен также ничего не с **SQLSetEnvAttr** вызывать, когда ведут себя, как ODBC *2.x* драйвера.  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Типы данных даты и времени](../../../odbc/reference/appendixes/datetime-data-types.md)  
  
-   [Обратная совместимость типов данных C](../../../odbc/reference/appendixes/backward-compatibility-of-c-data-types.md)  
  
-   [Закладки фиксированной длины](../../../odbc/reference/appendixes/fixed-length-bookmarks.md)  
  
-   [Поддержка SQLGetInfo](../../../odbc/reference/appendixes/sqlgetinfo-support.md)  
  
-   [Возврат SQL_NO_DATA](../../../odbc/reference/appendixes/returning-sql-no-data.md)  
  
-   [Вызов SQLSetPos для вставки данных](../../../odbc/reference/appendixes/calling-sqlsetpos-to-insert-data.md)  
  
-   [Загрузка по порядковому номеру](../../../odbc/reference/appendixes/loading-by-ordinal.md)
