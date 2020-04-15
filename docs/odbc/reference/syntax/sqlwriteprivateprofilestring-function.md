---
title: Функция S'LWritePrivateProfileString (ru) Документы Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLWritePrivateProfileString
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLWritePrivateProfileString
helpviewer_keywords:
- SQLWritePrivateProfileString [ODBC]
ms.assetid: 526f36a4-92ed-4874-9725-82d27c0b86f9
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: b0de5ad074fb2b760420686feddff58b26887112
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81286887"
---
# <a name="sqlwriteprivateprofilestring-function"></a>Функция SQLWritePrivateProfileString
**Соответствия**  
 Представлена версия: ODBC 2.0  
  
 **Сводка**  
 **СЗЛУТыртПриФпромсерверТальтнапишет** записывает имя значения и данные в подключку системы Odbc.ini.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
  
BOOL SQLWritePrivateProfileString(  
     LPCSTR     lpszSection,  
     LPCSTR     lpszEntry,  
     LPCSTR     lpszString,  
     LPCSTR     lpszFilename);  
```  
  
## <a name="arguments"></a>Аргументы  
 *lpszSection*  
 (Вход) Указывает на нулевую строку, содержащую название раздела, к которому строка будет скопирована. Если раздел не существует, он создается. Название раздела независит от дел; строка может быть любой комбинацией верхних и нижних букв.  
  
 *lpszEntry*  
 (Вход) Указывает на нулевую строку, содержащую имя ключа, связанного со строкой. Если ключ не существует в указанном разделе, он создается. Если этот аргумент NULL, весь раздел, включая все записи в разделе, удаляется.  
  
 *lpszString*  
 (Вход) Указывает на нулевую строку, которая должна быть написана в файл. Если этот аргумент является NULL, ключ, на который указывает аргумент *lpszEntry,* удаляется.  
  
 *lpszFilename*  
 (Выход) Указывает на нулевую строку, которая называет файл инициализации.  
  
## <a name="returns"></a>Результаты  
 Функция возвращает TRUE, если она успешна, FALSE, если она не удается.  
  
## <a name="diagnostics"></a>Диагностика  
 Когда **S'LWritePrivateProfileString** возвращает FALSE, связанное * \*значение pfErrorCode* можно получить, позвонив по **телефону S'LInstallerError.** В следующей таблице перечислены * \*значения pfErrorCode,* которые могут быть возвращены **S'LInstallerError,** и приведены в изъяны каждое из них в контексте этой функции.  
  
|*\*pfErrorCode*|Error|Описание|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_GENERAL_ERR|Общая ошибка установки|Произошла ошибка, для которой не было конкретной ошибки установки.|  
|ODBC_ERROR_REQUEST_FAILED|Не удалось выполнить запрос|Запрашиваемые системы информация не может быть написана.|  
|ODBC_ERROR_OUT_OF_MEM|Недостаточно памяти|Установщик не мог выполнить функцию из-за отсутствия памяти.|  
  
## <a name="comments"></a>Комментарии  
 **СЗЛУТырПриТПриПроцяжныйШнур** предоставляется как простой способ переноса драйверов и установки драйверов DLLs от Microsoft® Windows® microsoft Windows NT®/Windows 2000. Призывы к **WritePrivateProfileString,** которые пишут строку профиля в файл Odbc.ini должны быть заменены на звонки на **S'LWritePrivateProfileString**. **S'LWritePrivateProfileString** вызывает функции в API Win32® добавить указанное значение имени и данных в подключку системы Odbc.ini.  
  
 Режим конфигурации указывает, где в системе находится запись Odbc.ini, в которой перечислены значения DSN. Если DSN является пользователем DSN (переменная состояния USERDSN_ONLY), функция записывается в запись Odbc.ini в HKEY_CURRENT_USER. Если DSN является системой DSN (SYSTEMDSN_ONLY), функция записывает сяртам Odbc.ini в HKEY_LOCAL_MACHINE. Если переменная состояния является BOTHDSN, HKEY_CURRENT_USER пытаетсяся, и если она не удается, HKEY_LOCAL_MACHINE используется.  
  
## <a name="related-functions"></a>Связанные функции  
  
|Сведения о|См.|  
|---------------------------|---------|  
|Получение ценности из системной информации|[СЗЛГетПриТПрогрядТст](../../../odbc/reference/syntax/sqlgetprivateprofilestring-function.md)|
