---
title: Поведенческие изменения и ODBC 3.x Драйверы (ru) Документы Майкрософт
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
ms.openlocfilehash: 4d8343573261d74a6a0c652cf425b12da91f7cb0
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81292368"
---
# <a name="behavioral-changes-and-odbc-3x-drivers"></a>Изменения в поведении и драйверы ODBC 3.x
Атрибут среды SQL_ATTR_ODBC_VERSION указывает водителю, нужно ли ему демонстрировать поведение ODBC *2.x* или поведение ODBC *3.x.* Способ установки атрибута среды SQL_ATTR_ODBC_VERSION зависит от приложения. Приложения ODBC *3.x* должны позвонить в **S'LSetEnvAttr,** чтобы установить этот атрибут после того, как они вызовут **S'LAllocHandle** для выделения ручки среды и прежде чем они вызовут **S'LAllocHandle** для выделения ручки соединения. Если они не сделают этого, менеджер драйвера возвращает S'LSTATE HY010 (ошибка последовательности функций) на последнем вызове на **s'LAllocHandle**.  
  
> [!NOTE]  
>  Для получения дополнительной информации о поведенческих изменениях и действиях приложения [см.](../../../odbc/reference/develop-app/behavioral-changes.md)  
  
 Приложения ODBC *2.x* и приложения ODBC *2.x,* перекомполниваемые с файлами заголовка ODBC *3.x,* не вызываютs **S'LSetEnvAttr.** Тем не менее, вместо **s'LAllocHandle,** они вызывают **s'LAllocEnv** вместо S'LAllocHandle для выделения ручки среды. Поэтому, когда приложение вызывает **S'LAllocEnv** в менеджердрайвера, менеджер драйвера вызывает **s'LAllocHandle** и **S'LSetEnvAttr** в драйвере. Таким образом, драйверы ODBC *3.x* всегда могут рассчитывать на этот атрибут.  
  
 Если приложение, соответствующее стандартам, составленное с помощью ODBC_STD компилировать флаг, вызывает **s'LAllocEnv** (что может произойти из-за того, что **s'LAllocEnv** не амортизироваться в ISO), вызов отображается в **S'LAllocHandleStd** во время компиляции. В момент выполнения, приложение вызывает **S'LAllocHandleStd**. Менеджер драйвера устанавливает атрибут среды SQL_ATTR_ODBC_VERSION к SQL_OV_ODBC3. Звонок на **sLAllocHandleStd** эквивалентен вызову **в S'LAllocHandle** с *помощью HandleType* SQL_HANDLE_ENV и вызова в **S'LSetEnvAttr,** чтобы установить SQL_ATTR_ODBC_VERSION SQL_OV_ODBC3.  
  
 В некоторых архитектурах драйвера водителю необходимо отображаться как драйвер ODBC *2.x* или драйвер ODBC *3.x* в зависимости от соединения. Водитель в этом случае может быть не драйвером, а слоем, который находится между менеджером драйвера и другим драйвером. Например, он может имитировать драйвер, как ODBC Spy. В другом примере он может выступать в качестве шлюза, например, EDA/S'L. Чтобы появиться в качестве драйвера ODBC *3.x,* такой драйвер должен быть в состоянии экспортировать **S'LAllocHandle**, и появляться в качестве драйвера ODBC *2.x,* должны быть в состоянии экспортировать **S'LAllocConnect**, **S'LAllocEnv**, и **S'LAllocStmt**. При выделении среды, соединения или оператора менеджер драйвера проверяет, экспортирует ли этот драйвер **S'LAllocHandle.** Так как водитель делает это, менеджер драйвера вызывает **S'LAllocHandle** в драйвере. Если водитель работает с драйвером ODBC *2.x,* водитель должен в соответствии с необходимостью отобразить вызов на **s'LAllocHandle** в **S'LAllocConnect,** **S'LAllocEnv**, или **S'LAllocStmt.** Он также должен ничего не делать с вызовом **S'LSetEnvAttr,** когда он ведет себя как водитель ODBC *2.x.*  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Типы данных даты и времени](../../../odbc/reference/appendixes/datetime-data-types.md)  
  
-   [Обратная совместимость типов данных C](../../../odbc/reference/appendixes/backward-compatibility-of-c-data-types.md)  
  
-   [Закладки фиксированной длины](../../../odbc/reference/appendixes/fixed-length-bookmarks.md)  
  
-   [Поддержка SQLGetInfo](../../../odbc/reference/appendixes/sqlgetinfo-support.md)  
  
-   [Возврат SQL_NO_DATA](../../../odbc/reference/appendixes/returning-sql-no-data.md)  
  
-   [Вызов SQLSetPos для вставки данных](../../../odbc/reference/appendixes/calling-sqlsetpos-to-insert-data.md)  
  
-   [Загрузка по порядковому номеру](../../../odbc/reference/appendixes/loading-by-ordinal.md)
