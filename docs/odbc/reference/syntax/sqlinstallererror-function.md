---
title: "Функция SQLInstallerError | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- SQLInstallerError
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLInstallerError
helpviewer_keywords:
- SQLInstallerError [ODBC]
ms.assetid: e6474b79-4d55-458f-81ce-abfafe357f83
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: bb17b0ab5da8770c4622c7359c16de6876688c17
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="sqlinstallererror-function"></a>Функция SQLInstallerError
**Соответствия**  
 Появился в версии: ODBC 3.0  
  
 **Сводка**  
 **SQLInstallerError** возвращает сведениями о состоянии и ошибки для установщика функций ODBC.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
RETCODE SQLInstallerError(  
     WORD      iError,  
     DWORD *   pfErrorCode,  
     LPSTR     lpszErrorMsg,  
     WORD      cbErrorMsgMax,  
     WORD *    pcbErrorMsg);  
```  
  
## <a name="arguments"></a>Аргументы  
 *iError*  
 [Вход] Номер ошибки записи. Допустимые номера: от 1 до 8.  
  
 *pfErrorCode*  
 [Выход] Код ошибки установщика. (Дополнительные сведения см. в разделе «Комментарии».)  
  
 *lpszErrorMsg*  
 [Выход] Указатель хранилища для текста сообщения об ошибке.  
  
 *cbErrorMsgMax*  
 [Вход] Максимальная длина *szErrorMsg* буфера. Это должно быть меньше или равно SQL_MAX_MESSAGE_LENGTH конечное значение null знак «минус».  
  
 *cbErrorMsgMax*  
 [Вход] Максимальная длина *szErrorMsg* буфера. Это должно быть меньше или равно SQL_MAX_MESSAGE_LENGTH конечное значение null знак «минус».  
  
 *pcbErrorMsg*  
 [Выход] Указатель на общее количество байтов (за исключением знака завершения null) для возврата в *lpszErrorMsg*. Если количество байтов, доступных для возврата больше или равно *cbErrorMsgMax*, текст сообщения об ошибке в *lpszErrorMsg* усекается до *cbErrorMsgMax* минус байтов символов конечное значение NULL. *PcbErrorMsg* аргумент может быть пустой указатель.  
  
## <a name="returns"></a>Возвращает  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_NO_DATA или SQL_ERROR.  
  
## <a name="diagnostics"></a>Диагностика  
 **SQLInstallerError** не публикует значения погрешности для себя. **SQLInstallerError** вернет значение SQL_NO_DATA, если это не удается получить информацию об ошибках (в этом случае *pfErrorCode* не определено). Если **SQLInstallerError** не может получить доступ к значения ошибок по любой причине, который возвращает значение SQL_ERROR, **SQLInstallerError** возвращает значение SQL_ERROR, но не публикует все значения ошибки. Если вы не знаете длина строки предупреждение (*lpszErrorMsg*), можно задать *lpszErrorMsg* значение NULL, вызов **SQLInstallerError**. **SQLInstallerError** будет возвращается длина строки предупреждение в *cbErrorMsgMax*. Если буфер сообщения об ошибке слишком короткий **SQLInstallerError** возвращает SQL_SUCCESS_WITH_INFO, а правильный *pfErrorCode* значение для **SQLInstallerError**.  
  
 Чтобы определить, произошла ли усечения в сообщении об ошибке, приложение можно сравнить значение в *cbErrorMsgMax* аргумент фактическую длину текста сообщения записываются *pcbErrorMsg* аргумент. Если усечение происходит, длина правильно буфера должно быть выделено под *lpszErrorMsg* и **SQLInstallerError** должен вызываться с соответствующим свойством *iError*запись.  
  
## <a name="comments"></a>Комментарии  
 Приложение вызывает **SQLInstallerError** при предыдущим вызовом функции установщика ODBC возвращает значение FALSE. Функции установки установщика и драйвера или транслятор ODBC блога ноль или более ошибок только в том случае, если функция завершается с ошибкой (возвращает значение FALSE); Таким образом, приложение вызывает **SQLInstallerError** только после сбоя установки ODBC-функции.  
  
 Ошибка очереди установщика ODBC сбрасывается каждый раз, когда вызывается функция новый установщика. Таким образом приложение не может ожидать получения ошибок для функций, отличных от из последнего вызова функции установщика.  
  
 Чтобы получить несколько ошибок для вызова функции, приложение вызывает **SQLInstallerError** несколько раз.  
  
 Если нет дополнительных сведений, **SQLInstallerError** вернет значение SQL_NO_DATA, *pfErrorCode* аргумент не определен, *pcbErrorMsg* аргумент равен 0, и *lpszErrorMsg* аргумент содержит один символ завершения null (если не *cbErrorMsgMax* аргумент равен 0).

