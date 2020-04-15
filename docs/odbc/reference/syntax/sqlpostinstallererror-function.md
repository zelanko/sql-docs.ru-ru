---
title: Функция S'LPostInstallerОшибкаОшибка (ru) Документы Майкрософт
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: cdceff5c4e175ba9f135c6e5e4405933b1a86b7c
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306895"
---
# <a name="sqlpostinstallererror-function"></a>Функция SQLPostInstallerError
**Соответствия**  
 Представлена версия: ODBC 3.0  
  
 **Сводка**  
 **S'LPostInstallerError** предоставляет механизм для библиотеки настройки драйвера или переводчика для сообщения об ошибках **для функций ConfigDriver,** **ConfigDSN**и **ConfigTranslator** для очереди ошибок установки. Приложения не используют этот API; они используют **S'LInstallerError** для получения ошибки.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
  
RETCODE SQLPostInstallerError(  
     DWORD    fErrorCode,  
     LPSTR    szErrorMsg);  
```  
  
## <a name="arguments"></a>Аргументы  
 *fErrorCode*  
 (Вход) Код ошибки установки.  
  
 *szErrorMsg*  
 (Вход) Текст сообщения об ошибке.  
  
## <a name="returns"></a>Результаты  
 SQL_SUCCESS или SQL_ERROR.  
  
## <a name="diagnostics"></a>Диагностика  
 **S'LPostInstallerError** не публикует значения ошибок для себя. Если ошибка была успешно размещена в очереди ошибки установки (извлекаемая с помощью **S'LInstallerError),** SQL_SUCCESS возвращается. SQL_ERROR будет возвращен, если значение в аргументе *dwErrorCode* не является одним из указанных кодов ошибок установки.  
  
## <a name="related-functions"></a>Связанные функции  
  
|Сведения о|См.|  
|---------------------------|---------|  
|Добавление, изменение или удаление драйвера|[ConfigDriver](../../../odbc/reference/syntax/configdriver-function.md)|  
|Добавление, изменение или удаление источников данных|[Конфедерация](../../../odbc/reference/syntax/configdsn-function.md)|  
|Настройка опции перевода|[ConfigTranslator](../../../odbc/reference/syntax/configtranslator-function.md)|
