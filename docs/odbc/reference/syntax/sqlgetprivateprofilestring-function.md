---
title: Функция S'LGetPrivateProfileString (ru) Документы Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLGetPrivateProfileString
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLGetPrivateProfileString
helpviewer_keywords:
- SQLGetPrivateProfileString function [ODBC]
ms.assetid: b72ca065-4d67-48df-baac-e18379a8320a
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: c12fc8d08535960cbb239c14e017b2ad5faa6c0e
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81303296"
---
# <a name="sqlgetprivateprofilestring-function"></a>Функция SQLGetPrivateProfileString
**Соответствия**  
 Представлена версия: ODBC 2.0  
  
 **Сводка**  
 **S'LGetPrivateProfileString** получает список имен значений или данных, соответствующих значению системной информации.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
  
int SQLGetPrivateProfileString(  
     LPCSTR   lpszSection,  
     LPCSTR   lpszEntry,  
     LPCSTR   lpszDefault,  
     LPCSTR   RetBuffer,  
     INT      cbRetBuffer,  
     LPCSTR   lpszFilename);  
```  
  
## <a name="arguments"></a>Аргументы  
 *lpszSection*  
 (Вход) Указывает на строку с нулевым завершением, которая определяет раздел, содержащий ключевое имя. Если этот аргумент NULL, функция копирует все имена разделов в файле в поставляемый буфер.  
  
 *lpszEntry*  
 (Вход) Очки строки с нулевым завершением, содержащей ключевое имя, связанная строка которой должна быть извлечена. Если этот аргумент ЯВЛЯЕТСЯ NULL, все ключевые имена в разделе, указанном аргументом *lpszSection,* скопированы в буфер, указанный аргументом *RetBuffer.*  
  
 *lpszDefault*  
 (Вход) Указывает на нулевую строку, которая определяет значение по умолчанию для данного ключа, если ключ не может быть найден в файле инициализации. Этот аргумент не может иметь значение NULL.  
  
 *Ретбаффер*  
 (Выход) Указывает на буфер, который получает извлеченную строку.  
  
 *cbRetBuffer*  
 (Вход) Определяет размер, в символах, буфера, на который указывает аргумент *RetBuffer.*  
  
 *lpszFilename*  
 (Вход) Указывает на нулевую строку, которая называет файл инициализации. Если этот аргумент не содержит полного пути к файлу, выполняется поиск каталога по умолчанию.  
  
## <a name="returns"></a>Результаты  
 **S'LGetPrivateProfileString** возвращает целый номер, который указывает количество прочитанных символов.  
  
## <a name="diagnostics"></a>Диагностика  
 При сбывании вызова на вызов в **S'LGetPrivateProfileString** можно получить связанное * \*значение pfErrorCode,* позвонив по **телефону s'LInstallerError.** В следующей таблице перечислены * \*значения pfErrorCode,* которые могут быть возвращены **S'LInstallerError,** и приведены в изъяны каждое из них в контексте этой функции.  
  
|*\*pfErrorCode*|Error|Описание|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_GENERAL_ERR|Общая ошибка установки|Произошла ошибка, для которой не было конкретной ошибки установки.|  
|ODBC_ERROR_OUT_OF_MEM|Недостаточно памяти|Установщик не мог выполнить функцию из-за отсутствия памяти.|  
  
## <a name="comments"></a>Комментарии  
 **СЗЛГетПриТПриТизминг** предоставляется как простой способ переноса драйверов и установки драйверов DLL с Microsoft® Windows® microsoft Windows NT®/Windows 2000. Вызовы **для GetPrivateProfileString,** которые извлекают строку профиля из файла Odbc.ini, должны быть заменены вызовами на **S'LGetPrivateProfileString.** **S'LGetPrivateProfileString** вызывает функции в API Win32® для получения запрошенных имен значений или данных, соответствующих значению подключаемых данных Odbc.ini системной информации.  
  
 Режим конфигурации (по настройке **S'LSetConfigMode)** указывает, где в системе находится запись Odbc.ini, в которой перечислены значения DSN. Если DSN является пользователем DSN (режим конфигурации USERDSN_ONLY), функция читается с записи Odbc.ini в HKEY_CURRENT_USER. Если DSN является системой DSN (SYSTEMDSN_ONLY), функция читается из записи Odbc.ini в HKEY_LOCAL_MACHINE. Если режим конфигурации bothDSN, HKEY_CURRENT_USER пытаетсяся, и если он не удается, HKEY_LOCAL_MACHINE используется.  
  
## <a name="related-functions"></a>Связанные функции  
  
|Сведения о|См.|  
|---------------------------|---------|  
|Написание значения для системной информации|[СЗЛСНайтПритПритПрогрядТ](../../../odbc/reference/syntax/sqlwriteprivateprofilestring-function.md)|
