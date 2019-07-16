---
title: Функция SQLPostInstallerError | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 0d5e0a10b8c530494fa3c026be0d36fde066a97c
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68053669"
---
# <a name="sqlpostinstallererror-function"></a>Функция SQLPostInstallerError
**Соответствие стандартам**  
 Представленные версии: ODBC 3.0  
  
 **Сводка**  
 **SQLPostInstallerError** предоставляет механизм для установки библиотеки драйвера или перевода для сообщения об ошибках для **ConfigDriver**, **ConfigDSN**, и **ConfigTranslator**  функций в очередь ошибок установщика. Приложения не используют этот API; они используют **SQLInstallerError** извлекаемой ошибки.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
  
RETCODE SQLPostInstallerError(  
     DWORD    fErrorCode,  
     LPSTR    szErrorMsg);  
```  
  
## <a name="arguments"></a>Аргументы  
 *fErrorCode*  
 [Вход] Код ошибки установщика.  
  
 *szErrorMsg*  
 [Вход] Текст сообщения об ошибке.  
  
## <a name="returns"></a>Возвращает  
 Значение SQL_SUCCESS или SQL_ERROR.  
  
## <a name="diagnostics"></a>Диагностика  
 **SQLPostInstallerError** не размещайте значения погрешности для себя. Если ошибку учтена в очередь ошибок установщика (извлекаются с помощью **SQLInstallerError**), возвращается значение SQL_SUCCESS. Возвращает значение SQL_ERROR, если значение в *dwErrorCode* аргумент не является одним из кодов ошибок указанный установщик.  
  
## <a name="related-functions"></a>Связанные функции  
  
|Сведения о|См.|  
|---------------------------|---------|  
|Добавление, изменение или удаление драйвера.|[ConfigDriver](../../../odbc/reference/syntax/configdriver-function.md)|  
|Добавление, изменение или удаление источников данных|[ConfigDSN](../../../odbc/reference/syntax/configdsn-function.md)|  
|Установка параметра перевода|[ConfigTranslator](../../../odbc/reference/syntax/configtranslator-function.md)|
