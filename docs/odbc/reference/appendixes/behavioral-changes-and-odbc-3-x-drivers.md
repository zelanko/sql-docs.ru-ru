---
title: Изменения поведения и драйверы ODBC 3.x | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- sql_attr_odbc_version [ODBC]
- backward compatibility [ODBC], behavioral changes
- compatibility [ODBC], behavioral changes
ms.assetid: 88a503cc-bff7-42d9-83ff-8e232109ed06
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 2fe50cf12ce72ad3da5f9f2cb1f180d5875ef875
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="behavioral-changes-and-odbc-3x-drivers"></a>Изменения поведения и драйверы ODBC 3.x
Атрибут среды SQL_ATTR_ODBC_VERSION Указывает драйверу ли он должен достичь ODBC 2. *x* поведение или ODBC 3*.x* поведение. Как задать атрибут среды SQL_ATTR_ODBC_VERSION зависит от приложения. ODBC 3*.x* приложений необходимо вызвать **SQLSetEnvAttr** для установки этого атрибута после вызова они **SQLAllocHandle** выделить дескриптор среды и до вызова  **SQLAllocHandle** для выделения дескриптора соединения. Если они не сделано, диспетчер драйверов возвращает SQLSTATE HY010 (функция ошибка последовательности) при последнем вызове функции **SQLAllocHandle**.  
  
> [!NOTE]  
>  Дополнительные сведения о изменения поведения и действие приложения в разделе [изменения поведения](../../../odbc/reference/develop-app/behavioral-changes.md).  
  
 ODBC 2. *x* приложений и ODBC 2. *x* приложений повторная компиляция с ODBC 3*.x* файлы заголовков не следует вызывать **SQLSetEnvAttr**. Тем не менее, они вызвать **SQLAllocEnv** вместо **SQLAllocHandle** выделить дескриптор среды. Таким образом, когда приложение вызывает метод **SQLAllocEnv** диспетчера драйверов, диспетчер драйверов вызывает **SQLAllocHandle** и **SQLSetEnvAttr** в драйвере. Таким образом, ODBC 3*.x* драйверы всегда можно положиться на этот атрибут.  
  
 Если совместимый со стандартами приложение компилируется с помощью флага компиляции ODBC_STD вызовы **SQLAllocEnv** (которого может возникать, если **SQLAllocEnv** не является устаревшей в ISO), вызов сопоставляется  **SQLAllocHandleStd** во время компиляции. Во время выполнения, приложение вызывает **SQLAllocHandleStd**. Диспетчер драйверов устанавливает атрибут среды SQL_ATTR_ODBC_VERSION значение SQL_OV_ODBC3. Вызов **SQLAllocHandleStd** эквивалентен вызову для **SQLAllocHandle** с *HandleType* SQL_HANDLE_ENV и вызов **SQLSetEnvAttr** SQL_ATTR_ODBC_VERSION присваивается значение SQL_OV_ODBC3.  
  
 В некоторых архитектур драйвер необходим для драйвера отображаются как ODBC 2. *x* драйвера или ODBC 3*.x* драйвера, в зависимости от соединения. Драйвер в этом случае может оказаться фактически драйвер, но слой, на котором находится между диспетчером драйверов и еще один драйвер. Например он имитируют драйвер, такие как ODBC Spy. В другом примере он может выступать в качестве шлюза, как EDA/SQL. Отображение в виде ODBC 3*.x* драйвера, такой драйвер должен иметь возможность экспорта **SQLAllocHandle**и в виде ODBC 2. *x* драйвер, должен иметь возможность экспорта **SQLAllocConnect**, **SQLAllocEnv**, и **SQLAllocStmt**. Если среды, соединение или оператор должен быть выделен, диспетчер драйверов проверяет, экспортирует этот драйвер **SQLAllocHandle**. Так как драйвер, диспетчер драйверов вызывает **SQLAllocHandle** в драйвере. Если драйвер работает с ODBC 2. *x* драйвера, драйвер должен быть сопоставлен вызов **SQLAllocHandle** для **SQLAllocConnect**, **SQLAllocEnv**, или  **SQLAllocStmt**соответствующим образом. Он должен также ничего не с **SQLSetEnvAttr** вызывать при работает как ODBC 2. *x* драйвера.  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Типы данных даты и времени](../../../odbc/reference/appendixes/datetime-data-types.md)  
  
-   [Обратная совместимость типов данных C](../../../odbc/reference/appendixes/backward-compatibility-of-c-data-types.md)  
  
-   [Закладки фиксированной длины](../../../odbc/reference/appendixes/fixed-length-bookmarks.md)  
  
-   [Поддержка SQLGetInfo](../../../odbc/reference/appendixes/sqlgetinfo-support.md)  
  
-   [Возврат SQL_NO_DATA](../../../odbc/reference/appendixes/returning-sql-no-data.md)  
  
-   [Вызов SQLSetPos для вставки данных](../../../odbc/reference/appendixes/calling-sqlsetpos-to-insert-data.md)  
  
-   [Загрузка по порядковому номеру](../../../odbc/reference/appendixes/loading-by-ordinal.md)
