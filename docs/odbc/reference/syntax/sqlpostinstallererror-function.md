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
manager: craigg
ms.openlocfilehash: ac7fb545938a0ec5f212e9c0da867fbea5db4817
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "65536614"
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
