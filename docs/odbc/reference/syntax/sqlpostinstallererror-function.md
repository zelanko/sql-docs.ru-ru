---
title: Функция SQLPostInstallerError | Документы Microsoft
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
ms.topic: conceptual
apiname:
- SQLPostInstallerError
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLPostInstallerError
helpviewer_keywords:
- SQLPostInstallerError function [ODBC]
ms.assetid: 4c60d827-b2d2-4f27-b220-daa9e1fcdd8d
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 5ff4ce6578c2f62b840129f474b4a2aed7d1ff5b
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="sqlpostinstallererror-function"></a>Функция SQLPostInstallerError
**Соответствия**  
 Появился в версии: ODBC 3.0  
  
 **Сводка**  
 **SQLPostInstallerError** предоставляет механизм для библиотеки драйвера или преобразователь настройки отчетов об ошибках для **ConfigDriver**, **ConfigDSN**, и **ConfigTranslator**  функции очередь ошибок установщика. Приложения не используют этот интерфейс API; они используют **SQLInstallerError** для получения ошибки.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
RETCODE SQLPostInstallerError(  
     DWORD    fErrorCode,  
     LPSTR    szErrorMsg);  
```  
  
## <a name="arguments"></a>Аргументы  
 *fErrorCode*  
 [Вход] Код ошибки установщика.  
  
 *szErrorMsg*  
 [Вход] Текст сообщения об ошибке.  
  
## <a name="returns"></a>Возвращает  
 SQL_SUCCESS или SQL_ERROR.  
  
## <a name="diagnostics"></a>Диагностика  
 **SQLPostInstallerError** не публикует значения погрешности для себя. Если ошибка была успешно поставленных в очередь Ошибка установщика (извлекаемые с помощью **SQLInstallerError**), возвращается значение SQL_SUCCESS. Будет возвращено значение SQL_ERROR, если значение в *dwErrorCode* аргумент не является одним из кодов ошибок указанный установщик.  
  
## <a name="related-functions"></a>Связанные функции  
  
|Сведения о|См.|  
|---------------------------|---------|  
|Добавление, изменение или удаление драйвера|[ConfigDriver](../../../odbc/reference/syntax/configdriver-function.md)|  
|Добавление, изменение или удаление источников данных|[ConfigDSN](../../../odbc/reference/syntax/configdsn-function.md)|  
|Установка параметра преобразования|[ConfigTranslator](../../../odbc/reference/syntax/configtranslator-function.md)|
