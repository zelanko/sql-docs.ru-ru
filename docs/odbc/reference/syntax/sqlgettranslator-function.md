---
title: Функция SQLGetTranslator | Документация Майкрософт
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1f1c5bbfd2e2fbf91fd9e91acafe0bc72d006d3f
ms.sourcegitcommit: 6443f9a281904af93f0f5b78760b1c68901b7b8d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2018
ms.locfileid: "53209323"
---
# <a name="sqlgettranslator-function"></a>Функция SQLGetTranslator
**Соответствие стандартам**  
 Представленные версии: ODBC 2.0  
  
 **Сводка**  
 **SQLGetTranslator** отображает диалоговое окно, из которого пользователь может выбрать переводчика.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
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
 [Вход] Дескриптор родительского окна.  
  
 *lpszName*  
 [Вход/выход] Имя translator из информации о системе.  
  
 *cbNameMax*  
 [Вход] Максимальная длина *lpszName* буфера.  
  
 *pcbNameOut*  
 [Вход/выход] Общее число байтов (за исключением байтов конечное значение null), передать или возвращаются в *lpszName*. Если количество байтов, доступных для возврата больше или равно *cbNameMax*, имя переводчик в *lpszName* усекается до *cbNameMax* минус символ завершения NULL. *PcbNameOut* аргументом может быть пустым указателем.  
  
 *lpszPath*  
 [Выход] Полный путь к DLL перевода.  
  
 *cbPathMax*  
 [Вход] Максимальная длина *lpszPath* буфера.  
  
 *pcbPathOut*  
 [Выход] Общее число байтов (за исключением байтов конечное значение null) возвращаются в *lpszPath*. Если количество байтов, доступных для возврата больше или равно *cbPathMax*, путь к библиотеке DLL перевода в *lpszPath* усекается до *cbPathMax* минус символ завершения NULL. *PcbPathOut* аргументом может быть пустым указателем.  
  
 *pvOption*  
 [Выход] вариант перевода 32-разрядной.  
  
## <a name="returns"></a>Возвращает  
 Функция возвращает значение TRUE, если он успешно, и FALSE, если происходит сбой, или если пользователь отменил диалоговое окно.  
  
## <a name="diagnostics"></a>Диагностика  
 Когда **SQLGetTranslator** возвращает значение FALSE, связанным  *\*pfErrorCode* значение можно получить, вызвав **SQLInstallerError**. В следующей таблице перечислены  *\*pfErrorCode* значения, которые могут быть возвращены **SQLInstallerError** и объясняется каждый из них в контексте этой функции.  
  
|*\*pfErrorCode*|Ошибка|Описание|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_GENERAL_ERR|Ошибки общие установщика|Произошла ошибка для которой нет ошибок определенных установщика.|  
|ODBC_ERROR_INVALID_BUFF_LEN|Недопустимый буфер длины|*CbNameMax* или *cbPathMax* аргумент был меньше или равно 0.|  
|ODBC_ERROR_INVALID_HWND|Недопустимый дескриптор окна|*HwndParent* аргумент был недопустимым, или значение NULL.|  
|ODBC_ERROR_INVALID_NAME|Недопустимое имя драйвера или перевода|*LpszName* предоставил недопустимый аргумент. Он не будет найден в реестре.|  
|ODBC_ERROR_LOAD_LIBRARY_FAILED|Не удалось загрузить библиотеку установки драйвера или перевода|Не удалось загрузить библиотеку translator.|  
|ODBC_ERROR_INVALID_OPTION|Недопустимая транзакция параметр|*PvOption* аргумент содержал недопустимое значение.|  
|ODBC_ERROR_OUT_OF_MEM|Недостаточно памяти|Программа установки не удалось выполнить функцию из-за нехватки памяти.|  
  
## <a name="comments"></a>Комментарии  
 Если *hwndParent* имеет значение null или если *lpszName*, *lpszPath*, или *pvOption* является пустым указателем, **SQLGetTranslator** возвращает значение FALSE. В противном случае он отображает список установленных трансляторов в приведенное ниже диалоговое окно.  
  
 ![Диалоговое окно выбора переводчика](../../../odbc/reference/syntax/media/ch23j.gif "CH23J")  
  
 Если *lpszName* содержит имя допустимым translator он выбран. В противном случае \<нет Translator > выбран.  
  
 Если пользователь выбирает \<нет Translator >, содержимое *lpszName*, *lpszPath*, и *pvOption* не затронут. **SQLGetTranslator** задает *pcbNameOut* и *pcbPathOut* 0 и возвращает значение TRUE.  
  
 Если пользователь выбирает переводчика, **SQLGetTranslator** вызовы **ConfigTranslator** в DLL-файлов установки translator. Если **ConfigTranslator** возвращает значение FALSE, **SQLGetTranslator** возвращает его диалоговое окно. Если **ConfigTranslator** возвращает значение TRUE, **SQLGetTranslator** возвращает значение TRUE, вместе с параметром имя, путь и перевод выбранного перевода.  
  
## <a name="related-functions"></a>Связанные функции  
  
|Сведения о|См.|  
|---------------------------|---------|  
|Настройка переводчика|[ConfigTranslator](../../../odbc/reference/syntax/configtranslator-function.md)|  
|Получение атрибутов перевода|[SQLGetConnectAttr](../../../odbc/reference/syntax/sqlgetconnectattr-function.md)|  
|Установка атрибута перевода|[SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md)|
