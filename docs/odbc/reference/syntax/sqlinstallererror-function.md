---
title: Функция SQLInstallerError | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 2d5e05e62350d916e9c5fcf680af05717b39aa58
ms.sourcegitcommit: 6443f9a281904af93f0f5b78760b1c68901b7b8d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2018
ms.locfileid: "53208283"
---
# <a name="sqlinstallererror-function"></a>Функция SQLInstallerError
**Соответствие стандартам**  
 Представленные версии: ODBC 3.0  
  
 **Сводка**  
 **SQLInstallerError** возвращает сведения об ошибках и состоянии для установщика функций ODBC.  
  
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
 [Выход] Указатель на хранилище для текст сообщения об ошибке.  
  
 *cbErrorMsgMax*  
 [Вход] Максимальная длина *szErrorMsg* буфера. Это должно быть меньше или равно SQL_MAX_MESSAGE_LENGTH минус знак завершения null.  
  
 *cbErrorMsgMax*  
 [Вход] Максимальная длина *szErrorMsg* буфера. Это должно быть меньше или равно SQL_MAX_MESSAGE_LENGTH минус знак завершения null.  
  
 *pcbErrorMsg*  
 [Выход] Указатель на общее число байтов (за исключением знака завершения null) для возврата в *lpszErrorMsg*. Если количество байтов, доступных для возврата больше или равно *cbErrorMsgMax*, текст сообщения об ошибке в *lpszErrorMsg* усекается до *cbErrorMsgMax* минус байтов символов конечное значение NULL. *PcbErrorMsg* аргументом может быть пустым указателем.  
  
## <a name="returns"></a>Возвращает  
 Значение SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_NO_DATA или SQL_ERROR.  
  
## <a name="diagnostics"></a>Диагностика  
 **SQLInstallerError** не размещайте значения погрешности для себя. **SQLInstallerError** вернет значение SQL_NO_DATA, если она не может получить все сведения об ошибке (в этом случае *pfErrorCode* не определено). Если **SQLInstallerError** недоступен по любой причине, который возвращает значение SQL_ERROR, ошибочные значения **SQLInstallerError** возвращает значение SQL_ERROR, но не размещайте значения ошибки. Если вы не знаете длину строки предупреждение (*lpszErrorMsg*), можно задать *lpszErrorMsg* значение NULL и вызов **SQLInstallerError**. **SQLInstallerError** будет возвращается длина строки предупреждение в *cbErrorMsgMax*. Если буфер сообщения об ошибке слишком короткий, **SQLInstallerError** возвращает SQL_SUCCESS_WITH_INFO и возвращает правильную *pfErrorCode* значение **SQLInstallerError**.  
  
 Чтобы определить, произошла ли усечения в сообщении об ошибке, приложение можно сравнить значение в *cbErrorMsgMax* аргумент фактическую длину текст сообщения, записываемый *pcbErrorMsg* аргумент. Если усечение происходит, длина буфера правильный должно быть выделено под *lpszErrorMsg* и **SQLInstallerError** должен вызываться с соответствующим *iError*записи.  
  
## <a name="comments"></a>Комментарии  
 Приложение вызывает **SQLInstallerError** после предыдущего вызова функции установщика ODBC возвращает значение FALSE. Функции ODBC, установщика и драйвера или translator установки блога ноль или более ошибок, только в том случае, если функция завершается с ошибкой (возвращает значение FALSE); Таким образом, приложение вызывает **SQLInstallerError** только в том случае, после сбоя установки ODBC-функции.  
  
 В очередь ошибок установщика ODBC очищается при каждом вызове функции нового установщика. Таким образом приложения не может ожидать получения ошибок для функций, отличных от из последнего вызова функции установщика.  
  
 Чтобы получить несколько ошибок для вызова функции, приложение вызывает **SQLInstallerError** несколько раз.  
  
 При наличии нет дополнительных сведений **SQLInstallerError** вернет значение SQL_NO_DATA, *pfErrorCode* аргумента не определено, *pcbErrorMsg* аргумент равен 0, и *lpszErrorMsg* аргумент содержит один символ завершения null (если только не *cbErrorMsgMax* аргумент равен 0).
