---
title: Функция ConfigTranslator | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
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
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 4a415d5c1a650f4a5c9b40373cf74f41f0c9fc5b
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="configtranslator-function"></a>Функция ConfigTranslator
**Соответствия**  
 Появился в версии: ODBC 2.0  
  
 **Сводка**  
 **ConfigTranslator** возвращает перевод параметр по умолчанию для преобразователя. Он может быть в преобразователь DLL или отдельных DLL-файлов установки.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
BOOL ConfigTranslator(  
     HWND     hwndParent,  
     DWORD *  pvOption);  
```  
  
## <a name="arguments"></a>Аргументы  
 *hwndParent*  
 [Вход] Дескриптор родительского окна. Функция не будет отображать все диалоговые окна, если маркер имеет значение null.  
  
 *pvOption*  
 [Выход] Этот параметр из 32-разрядных перевода.  
  
## <a name="returns"></a>Возвращает  
 Функция возвращает значение TRUE, если он прошел успешно, FALSE в случае неудачи.  
  
## <a name="diagnostics"></a>Диагностика  
 Когда **ConfigTranslator** возвращает значение FALSE, связанный с ним  *\*pfErrorCode* значение передается буфера установщика ошибок с помощью вызова **SQLPostInstallerError**и может быть получен путем вызова **SQLInstallerError**. В следующей таблице перечислены  *\*pfErrorCode* значения, которые могут быть возвращены **SQLInstallerError** и описание каждого из них в контексте этой функции.  
  
|*\*pfErrorCode*|Ошибка|Описание|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_INVALID_HWND|Недопустимый дескриптор окна|*HwndParent* аргумент имеет недопустимый или NULL.|  
|ODBC_ERROR_DRIVER_SPECIFIC|Ошибка драйвера или преобразователь|Ошибка драйвера, для которого нет определенных ошибок установщика ODBC. *SzError* аргумента в вызове **SQLPostInstallerError** функция должна содержать сообщении об ошибке драйвера.|  
|ODBC_ERROR_INVALID_OPTION|Недопустимое преобразование параметра|*PvOption* аргумент содержит недопустимое значение.|  
  
## <a name="comments"></a>Комментарии  
 Если преобразователь поддерживает только один перевод параметр **ConfigTranslator** возвращает значение TRUE и задает *pvOption* для 32-разрядный параметр. В противном случае он определяет параметр преобразования по умолчанию для использования. **ConfigTranslator** можно отобразить диалоговое окно, с помощью которого пользователь выбирает параметр преобразования по умолчанию.  
  
## <a name="related-functions"></a>Связанные функции  
  
|Сведения о|См.|  
|---------------------------|---------|  
|Получение параметр миграции|[SQLGetConnectAttr](../../../odbc/reference/syntax/sqlgetconnectattr-function.md)|  
|При выборе переводчика|[SQLGetTranslator](../../../odbc/reference/syntax/sqlgettranslator-function.md)|  
|Установка параметра преобразования|[SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md)|
