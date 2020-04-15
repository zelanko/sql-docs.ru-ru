---
title: Функция S'LGetTranslator (ru) Документы Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLGetTranslator
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLGetTranslator
helpviewer_keywords:
- SQLGetTranslator function [ODBC]
ms.assetid: 33879db3-5ef9-4585-9be5-69376157e017
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: bcd5aeebab8539b8b94db56ff30892f4a7dbbac1
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81303275"
---
# <a name="sqlgettranslator-function"></a>Функция SQLGetTranslator
**Соответствия**  
 Представлена версия: ODBC 2.0  
  
 **Сводка**  
 **СЗЛГетПереводчик** отображает диалоговую коробку, из которой пользователь может выбрать переводчика.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
  
BOOL SQLGetTranslator(  
     HWND      hwndParent,  
     LPSTR     lpszName,  
     WORD      cbNameMax,  
     WORD *    pcbNameOut,  
     LPSTR     lpszPath,  
     WORD      cbPathMax,  
     WORD *    pcbPathOut,  
     DWORD *   pvOption);  
```  
  
## <a name="arguments"></a>Аргументы  
 *hwndParent*  
 (Вход) Ручка родительского окна.  
  
 *lpszName*  
 (Вход/выход) Имя переводчика из системной информации.  
  
 *cbNameMax*  
 (Вход) Максимальная длина буфера *lpszName.*  
  
 *pcbNameOut*  
 (Вход/выход) Общее количество байтов (за исключением байт-ра-на-а-а-- не было отменено) пройдено или возвращено в *lpszName*. Если количество байтов, доступных для возврата, больше или равно *cbNameMax,* имя переводчика в *lpszName* усечено до *cbNameMax* за вычетом символа нулевого прекращения. Аргумент *pcbNameOut* может быть нулевой указатель.  
  
 *lpszPath*  
 (Выход) Полный путь перевода DLL.  
  
 *cbPathMax*  
 (Вход) Максимальная длина буфера *lpszPath.*  
  
 *pcbPathOut*  
 (Выход) Общее количество байтов (за исключением байт-навили) возвращается в *lpszPath*. Если количество байтов, доступных для возврата, больше или равно *cbPathMax,* путь DLL перевода в *lpszPath* усечен *до cbPathMax* за вычетом символа нулевого прекращения. Аргумент *pcbPathOut* может быть нулевым указателем.  
  
 *pvOption*  
 32-битный вариант перевода.  
  
## <a name="returns"></a>Результаты  
 Функция возвращает TRUE, если она успешна, FALSE, если она не удается или если пользователь отменяет диалоговое окно.  
  
## <a name="diagnostics"></a>Диагностика  
 Когда **S'LGetTranslator** возвращает FALSE, связанное * \*значение pfErrorCode* можно получить, позвонив по **телефону S'LInstallerError.** В следующей таблице перечислены * \*значения pfErrorCode,* которые могут быть возвращены **S'LInstallerError,** и приведены в изъяны каждое из них в контексте этой функции.  
  
|*\*pfErrorCode*|Error|Описание|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_GENERAL_ERR|Общая ошибка установки|Произошла ошибка, для которой не было конкретной ошибки установки.|  
|ODBC_ERROR_INVALID_BUFF_LEN|Недействительная длина буфера|Аргумент *cbNameMax* или *cbPathMax* был меньше или равен 0.|  
|ODBC_ERROR_INVALID_HWND|Недействительная ручка окна|Аргумент *hwndParent* был недействительным или NULL.|  
|ODBC_ERROR_INVALID_NAME|Имя недействительного водителя или переводчика|Аргумент *lpszName* был недействительным. Его не удалось найти в реестре.|  
|ODBC_ERROR_LOAD_LIBRARY_FAILED|Не удалось загрузить библиотеку установки драйвера или переводчика|Библиотека переводчика не могла быть загружена.|  
|ODBC_ERROR_INVALID_OPTION|Недействительный параметр транзакции|Аргумент *pvOption* содержал недействительное значение.|  
|ODBC_ERROR_OUT_OF_MEM|Недостаточно памяти|Установщик не мог выполнить функцию из-за отсутствия памяти.|  
  
## <a name="comments"></a>Комментарии  
 Если *hwndParent* является недействительным или если *lpszName*, *lpszPath*, или *pvOption* является нулевой указатель, **S'LGetTranslator** возвращает FALSE. В противном случае он отображает список установленных переводчиков в следующем диалоговом окне.  
  
 ![Диалоговое окно выбора переводчика](../../../odbc/reference/syntax/media/ch23j.gif "CH23J")  
  
 Если *lpszName* содержит действительное имя переводчика, оно выбрано. В \<противном случае не выбирается> переводчика.  
  
 Если пользователь выбирает \<No Translator>, содержимое *lpszName,* *lpszPath*и *pvOption* не трогают. **СЗЛГетПереводчик** устанавливает *pcbNameOut* и *pcbPathOut* до 0 и возвращает TRUE.  
  
 Если пользователь выбирает переводчика, **S'LGetTranslator** вызывает **ConfigTranslator** в настройке DLL переводчика. Если **ConfigTranslator** возвращает FALSE, **S'LGetTranslator** возвращается в диалоговую будку. Если **ConfigTranslator** возвращает TRUE, **S'LGetTranslator** возвращает TRUE вместе с выбранным именем переводчика, маршрутом и вариантом перевода.  
  
## <a name="related-functions"></a>Связанные функции  
  
|Сведения о|См.|  
|---------------------------|---------|  
|Настройка переводчика|[ConfigTranslator](../../../odbc/reference/syntax/configtranslator-function.md)|  
|Получение атрибута перевода|[SQLGetConnectAttr](../../../odbc/reference/syntax/sqlgetconnectattr-function.md)|  
|Установка атрибута перевода|[SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md)|
