---
title: Функция ConfigTranslator Документы Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- ConfigTranslator
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- ConfigTranslator
helpviewer_keywords:
- ConfigTranslator [ODBC]
ms.assetid: 7c22f07e-36de-425b-aa67-e32a84afae92
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: fb2f26f87854d74a217885010014633963472787
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306035"
---
# <a name="configtranslator-function"></a>Функция ConfigTranslator
**Соответствия**  
 Представлена версия: ODBC 2.0  
  
 **Сводка**  
 **ConfigTranslator** возвращает переводчику опцию перевода по умолчанию. Это может быть в переводчике DLL или отдельной установке DLL.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
  
BOOL ConfigTranslator(  
     HWND     hwndParent,  
     DWORD *  pvOption);  
```  
  
## <a name="arguments"></a>Аргументы  
 *hwndParent*  
 (Вход) Ручка родительского окна. Функция не будет отображать диалоговые коробки, если ручка недействительна.  
  
 *pvOption*  
 (Выход) Вариант 32-битного перевода.  
  
## <a name="returns"></a>Результаты  
 Функция возвращает TRUE, если она успешна, FALSE, если она не удается.  
  
## <a name="diagnostics"></a>Диагностика  
 Когда **ConfigTranslator** возвращает FALSE, связанное * \*значение pfErrorCode* размещается в буфере ошибки установки по вызову на **s'LPostInstallerError** и может быть получено по телефону **S'LInstallerError.** В следующей таблице перечислены * \*значения pfErrorCode,* которые могут быть возвращены **S'LInstallerError,** и приведены в изъяны каждое из них в контексте этой функции.  
  
|*\*pfErrorCode*|Error|Описание|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_INVALID_HWND|Недействительная ручка окна|Аргумент *hwndParent* был недействительным или NULL.|  
|ODBC_ERROR_DRIVER_SPECIFIC|Ошибка водителя или переводчика|Ошибка, связанная с драйвером, для которой нет определенной ошибки установки ODBC. Аргумент *SzError* в вызове к функции **S'LPostInstallerError** должен содержать сообщение об ошибке, конкретное для драйвера.|  
|ODBC_ERROR_INVALID_OPTION|Недействительный вариант перевода|Аргумент *pvOption* содержал недействительное значение.|  
  
## <a name="comments"></a>Комментарии  
 Если переводчик поддерживает только один вариант перевода, **ConfigTranslator** возвращает TRUE и устанавливает *pvOption* на 32-битный вариант. В противном случае он определяет вариант перевода по умолчанию для использования. **ConfigTranslator** может отображать диалоговую коробку, с помощью которой пользователь выбирает вариант перевода по умолчанию.  
  
## <a name="related-functions"></a>Связанные функции  
  
|Сведения о|См.|  
|---------------------------|---------|  
|Получение опции перевода|[SQLGetConnectAttr](../../../odbc/reference/syntax/sqlgetconnectattr-function.md)|  
|Выбор переводчика|[СЗЛГетПереводчик](../../../odbc/reference/syntax/sqlgettranslator-function.md)|  
|Настройка опции перевода|[SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md)|
