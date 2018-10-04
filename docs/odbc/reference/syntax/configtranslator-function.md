---
title: Функция ConfigTranslator | Документация Майкрософт
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f38a9c6814c65593ab452e646a8b1f184e2095de
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47676582"
---
# <a name="configtranslator-function"></a>Функция ConfigTranslator
**Соответствие стандартам**  
 Версия была введена: ODBC 2.0  
  
 **Сводка**  
 **ConfigTranslator** возвращает вариант перевода по умолчанию для преобразователя. Он может находиться в translator DLL или отдельные DLL-файлов установки.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
BOOL ConfigTranslator(  
     HWND     hwndParent,  
     DWORD *  pvOption);  
```  
  
## <a name="arguments"></a>Аргументы  
 *hwndParent*  
 [Вход] Дескриптор родительского окна. Функция не будет отображать все диалоговые окна, если дескриптор имеет значение null.  
  
 *pvOption*  
 [Выход] Это вариант перевода 32-разрядной.  
  
## <a name="returns"></a>Возвращает  
 Функция возвращает значение TRUE при успешном выполнении, FALSE в случае неудачи.  
  
## <a name="diagnostics"></a>Диагностика  
 Когда **ConfigTranslator** возвращает значение FALSE, связанным  *\*pfErrorCode* передано значение в буфер Ошибка установщика с помощью вызова **SQLPostInstallerError**и может быть получен путем вызова **SQLInstallerError**. В следующей таблице перечислены  *\*pfErrorCode* значения, которые могут быть возвращены **SQLInstallerError** и объясняется каждый из них в контексте этой функции.  
  
|*\*pfErrorCode*|Ошибка|Описание|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_INVALID_HWND|Недопустимый дескриптор окна|*HwndParent* аргумент был недопустимым, или значение NULL.|  
|ODBC_ERROR_DRIVER_SPECIFIC|Ошибка драйвера или перевода|Ошибка драйвера, для которого отсутствуют определенные ошибки установщика ODBC. *SzError* аргумента в вызове **SQLPostInstallerError** функция должна содержать сообщении об ошибке специфические для драйвера.|  
|ODBC_ERROR_INVALID_OPTION|Недопустимое преобразование параметр|*PvOption* аргумент содержал недопустимое значение.|  
  
## <a name="comments"></a>Комментарии  
 Если преобразователь поддерживает только одним переводом, **ConfigTranslator** возвращает значение TRUE и задает *pvOption* для 32-битовое шифрование. В противном случае он определяет параметр преобразования по умолчанию для использования. **ConfigTranslator** можно отобразить диалоговое окно, с помощью которого пользователь выбирает вариант перевода по умолчанию.  
  
## <a name="related-functions"></a>Связанные функции  
  
|Сведения о|См.|  
|---------------------------|---------|  
|Получение параметр миграции|[SQLGetConnectAttr](../../../odbc/reference/syntax/sqlgetconnectattr-function.md)|  
|Выбрав переводчика|[SQLGetTranslator](../../../odbc/reference/syntax/sqlgettranslator-function.md)|  
|Установка параметра перевода|[SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md)|
