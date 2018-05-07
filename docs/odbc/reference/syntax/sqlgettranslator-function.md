---
title: Функция SQLGetTranslator | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
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
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 803e823de76deba750dc188c2f01e69b0a2f84db
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="sqlgettranslator-function"></a>Функция SQLGetTranslator
**Соответствия**  
 Появился в версии: ODBC 2.0  
  
 **Сводка**  
 **SQLGetTranslator** отображает диалоговое окно, из которого пользователь может выбрать транслятор.  
  
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
 [Вход/выход] Имя преобразователь из сведений о системе.  
  
 *cbNameMax*  
 [Вход] Максимальная длина *lpszName* буфера.  
  
 *pcbNameOut*  
 [Вход/выход] Общее число байтов (за исключением байтов конечное значение null) передавать или возвращать в *lpszName*. Если количество байтов, доступных для возврата больше или равно *cbNameMax*, имя преобразователь в *lpszName* усекается до *cbNameMax* минус знак завершения NULL. *PcbNameOut* аргумент может быть пустой указатель.  
  
 *lpszPath*  
 [Выход] Полный путь к DLL перевода.  
  
 *cbPathMax*  
 [Вход] Максимальная длина *lpszPath* буфера.  
  
 *pcbPathOut*  
 [Выход] Общее число байтов (за исключением байтов конечное значение null) возвращается в *lpszPath*. Если количество байтов, доступных для возврата больше или равно *cbPathMax*, путь к DLL перевода в *lpszPath* усекается до *cbPathMax* минус знак завершения NULL. *PcbPathOut* аргумент может быть пустой указатель.  
  
 *pvOption*  
 [Выход] преобразования 32-разрядных параметр.  
  
## <a name="returns"></a>Возвращает  
 Функция возвращает значение TRUE, если завершена успешно, и FALSE в случае неудачи, или если пользователь отменяет диалоговое окно.  
  
## <a name="diagnostics"></a>Диагностика  
 Когда **SQLGetTranslator** возвращает значение FALSE, связанный с ним  *\*pfErrorCode* значение можно получить путем вызова **SQLInstallerError**. В следующей таблице перечислены  *\*pfErrorCode* значения, которые могут быть возвращены **SQLInstallerError** и описание каждого из них в контексте этой функции.  
  
|*\*pfErrorCode*|Ошибка|Описание|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_GENERAL_ERR|Установщик Общие ошибки|Произошла ошибка для которого нет ошибок определенного установщика.|  
|ODBC_ERROR_INVALID_BUFF_LEN|Недопустимый буфер длины|*CbNameMax* или *cbPathMax* аргумент был меньше или равно 0.|  
|ODBC_ERROR_INVALID_HWND|Недопустимый дескриптор окна|*HwndParent* аргумент имеет недопустимый или NULL.|  
|ODBC_ERROR_INVALID_NAME|Недопустимое имя драйвера или преобразователь|*LpszName* недопустимый аргумент. Он не найден в реестре.|  
|ODBC_ERROR_LOAD_LIBRARY_FAILED|Не удалось загрузить библиотеку установки драйвера или преобразователь|Не удается загрузить библиотеку преобразователя.|  
|ODBC_ERROR_INVALID_OPTION|Параметр Недопустимая транзакция|*PvOption* аргумент содержит недопустимое значение.|  
|ODBC_ERROR_OUT_OF_MEM|Недостаточно памяти|Программе установки не удалось выполнить функцию из-за нехватки памяти.|  
  
## <a name="comments"></a>Комментарии  
 Если *hwndParent* имеет значение null или если *lpszName*, *lpszPath*, или *pvOption* является пустым указателем, **SQLGetTranslator** возвращает значение FALSE. В противном случае он отображает список установленных трансляторы в диалоговом окне.  
  
 ![Диалоговое окно выберите транслятор](../../../odbc/reference/syntax/media/ch23j.gif "CH23J")  
  
 Если *lpszName* содержит имя допустимым переводчик он выбран. В противном случае \<транслятор не используется > выбран.  
  
 Если пользователь выберет \<транслятор не используется >, содержимое *lpszName*, *lpszPath*, и *pvOption* не затрагивает. **SQLGetTranslator** задает *pcbNameOut* и *pcbPathOut* 0 и возвращает значение TRUE.  
  
 Если пользователь выберет транслятор, **SQLGetTranslator** вызовы **ConfigTranslator** в DLL-файлов установки переводчик. Если **ConfigTranslator** возвращает FALSE, **SQLGetTranslator** возвращается в свое диалоговое окно. Если **ConfigTranslator** возвращает значение TRUE, **SQLGetTranslator** возвращает значение TRUE, вместе с параметром выбранного транслятора имя, путь и преобразования.  
  
## <a name="related-functions"></a>Связанные функции  
  
|Сведения о|См.|  
|---------------------------|---------|  
|Настройка переводчика|[ConfigTranslator](../../../odbc/reference/syntax/configtranslator-function.md)|  
|Получение атрибутов перевода|[SQLGetConnectAttr](../../../odbc/reference/syntax/sqlgetconnectattr-function.md)|  
|С помощью атрибута перевода|[SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md)|
