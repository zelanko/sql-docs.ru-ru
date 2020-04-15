---
title: Функция S'LRemoveDSNFromIni (ru) Документы Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLRemoveDSNFromIni
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLRemoveDSNFromIni
helpviewer_keywords:
- SQLRemoveDSNFromIni function [ODBC]
ms.assetid: bb2e8273-7b61-4113-bfc8-f7ccc607c811
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 848e82741954ab24941d5d519699292727ca25d6
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81301803"
---
# <a name="sqlremovedsnfromini-function"></a>Функция SQLRemoveDSNFromIni
**Соответствия**  
 Представлена версия: ODBC 1.0  
  
 **Сводка**  
 **S'LRemoveDSNFromIni** удаляет источник данных из системной информации.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
  
BOOL SQLRemoveDSNFromIni(  
     LPCSTR   lpszDSN);  
```  
  
## <a name="arguments"></a>Аргументы  
 *lpszDSN*  
 (Вход) Имя источника данных для удаления.  
  
## <a name="returns"></a>Результаты  
 Функция возвращает TRUE, если она удаляет источник данных или источник данных не был в файле Odbc.ini. Он возвращает FALSE, если он не удаляет источник данных.  
  
## <a name="diagnostics"></a>Диагностика  
 Когда **S'LRemoveDSNFromIni** возвращает FALSE, связанное * \*значение pfErrorCode* можно получить, позвонив по **телефону S'LInstallerError.** В следующей таблице перечислены * \*значения pfErrorCode,* которые могут быть возвращены **S'LInstallerError,** и приведены в изъяны каждое из них в контексте этой функции.  
  
|*\*pfErrorCode*|Error|Описание|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_GENERAL_ERR|Общая ошибка установки|Произошла ошибка, для которой не было конкретной ошибки установки.|  
|ODBC_ERROR_INVALID_DSN|Недействительный DSN|Аргумент *lpszDSN* был недействительным.|  
|ODBC_ERROR_REQUEST_FAILED|Не удалось выполнить запрос|Установщик не смог удалить информацию DSN из реестра.|  
|ODBC_ERROR_OUT_OF_MEM|Недостаточно памяти|Установщик не мог выполнить функцию из-за отсутствия памяти.|  
  
## <a name="comments"></a>Комментарии  
 **S'LRemoveDSNFromIni** удаляет название источника данных из раздела «Источники данных ODBC» в системе информации. Он также удаляет раздел спецификации источника данных из системной информации.  
  
 Эта функция должна вызываться только из библиотеки установки драйвера.  
  
## <a name="related-functions"></a>Связанные функции  
  
|Сведения о|См.|  
|---------------------------|---------|  
|Добавление, изменение или удаление источника данных|[Конфедерация](../../../odbc/reference/syntax/configdsn-function.md)|  
|Добавление, изменение или удаление источника данных|[SQLConfigDataSource](../../../odbc/reference/syntax/sqlconfigdatasource-function.md)|  
|Удаление источника данных по умолчанию|[СЗЛУдалениеDefaultDataИсточник](../../../odbc/reference/syntax/sqlremovedefaultdatasource-function.md)|  
|Добавление имени источника данных в системную информацию|[СЗЛДуНТСНОниИ](../../../odbc/reference/syntax/sqlwritedsntoini-function.md)|
