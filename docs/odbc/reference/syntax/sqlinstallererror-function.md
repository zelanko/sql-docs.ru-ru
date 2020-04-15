---
title: Функция S'LInstallerError Error (ru) Документы Майкрософт
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: e749237cf87c5054b8273f38531d9336d316e040
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81302105"
---
# <a name="sqlinstallererror-function"></a>Функция SQLInstallerError
**Соответствия**  
 Представлена версия: ODBC 3.0  
  
 **Сводка**  
 **S'LInstallerError** возвращает информацию об ошибке или статусе для функций установки ODBC.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
  
RETCODE SQLInstallerError(  
     WORD      iError,  
     DWORD *   pfErrorCode,  
     LPSTR     lpszErrorMsg,  
     WORD      cbErrorMsgMax,  
     WORD *    pcbErrorMsg);  
```  
  
## <a name="arguments"></a>Аргументы  
 *iError*  
 (Вход) Номер записи ошибки. Действительные номера от 1 до 8.  
  
 *pfErrorCode*  
 (Выход) Код ошибки установки. (Для получения дополнительной информации, см. "Комментарии.")  
  
 *lpszErrorMsg*  
 (Выход) Указатель на хранение текста сообщения об ошибке.  
  
 *cbErrorMsgMax*  
 (Вход) Максимальная длина буфера *szErrorMsg.* Это должно быть меньше или равно SQL_MAX_MESSAGE_LENGTH минус символ нулевого прекращения.  
  
 *cbErrorMsgMax*  
 (Вход) Максимальная длина буфера *szErrorMsg.* Это должно быть меньше или равно SQL_MAX_MESSAGE_LENGTH минус символ нулевого прекращения.  
  
 *pcbErrorMsg*  
 (Выход) Указатель на общее количество байтов (за исключением символа нулевого прекращения) можно вернуть в *lpszErrorMsg*. Если количество байтов, доступных для возврата, больше или равно *cbErrorMsgMax,* текст сообщения об ошибке в *lpszErrorMsg* усечен до *cbErrorMsgMax* минус байты символа нулевого прекращения. *PCbErrorMsg* аргумент может быть нулевой указатель.  
  
## <a name="returns"></a>Результаты  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_NO_DATA или SQL_ERROR.  
  
## <a name="diagnostics"></a>Диагностика  
 **S'LInstallerError** не публикует значения ошибок для себя. **S'LInstallerError** возвращает SQL_NO_DATA, когда он не в состоянии получить любую информацию об ошибках (в этом случае *pfErrorCode* не определен). Если **S'LInstallerError** не может получить доступ к значениям ошибок по любой причине, которая обычно возвращается SQL_ERROR, **S'LInstallerError** возвращает SQL_ERROR но не публикует значения ошибок. Если вы не знаете длину строки предупреждения *(lpszErrorMsg),* вы можете установить *lpszErrorMsg* в NULL и позвонить в **S'LInstallerError.** **S'LInstallerError** затем вернет длину строки предупреждения в *cbErrorMsgMax*. Если буфер для сообщения об ошибке слишком короткий, **S'LInstallerError** возвращает SQL_SUCCESS_WITH_INFO и возвращает правильное значение *pfErrorCode* для **S'LInstallerError.**  
  
 Чтобы определить, произошла ли усечение в сообщении об ошибке, приложение может сравнить значение в аргументе *cbErrorMsgMax* с фактической длиной текста сообщения, написанного в *аргументе pcbErrorMsg.* Если усечение происходит, правильная длина буфера должна быть выделена для *lpszErrorMsg* и **S'LInstallerError** должен быть вызван снова с соответствующей записью *iError.*  
  
## <a name="comments"></a>Комментарии  
 Приложение вызывает **S'LInstallerError,** когда предыдущий звонок в функцию установки ODBC возвращает FALSE. Установщик ODBC и функция установки драйвера или переводчика после нулевых или более ошибок только в случае сбоя функции (возвращает FALSE); Таким образом, приложение вызывает **S'LInstallerError** только после того, как функция установки ODBC выходит из строя.  
  
 Очередь ошибки установки ODBC смывается каждый раз, когда вызывается новая функция установки. Таким образом, приложение не может ожидать, чтобы получить ошибки для функций, кроме от последнего вызова функции установки.  
  
 Чтобы извлечь несколько ошибок для вызова функции, приложение несколько раз вызывает **S'LInstallerError.**  
  
 Когда нет дополнительной информации, **S'LInstallerError** возвращается SQL_NO_DATA, аргумент *pfErrorCode* не определен, аргумент *pcbErrorMsg* равен 0, а аргумент *lpszErrorMsg* содержит один символ нулевого прекращения (если аргумент *cbErrorMsgMax* не равен 0).
