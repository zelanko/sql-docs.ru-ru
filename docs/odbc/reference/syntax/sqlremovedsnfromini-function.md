---
title: Функция Склремоведснфромини | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLRemoveDSNFromIni
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLRemoveDSNFromIni
helpviewer_keywords:
- SQLRemoveDSNFromIni function [ODBC]
ms.assetid: bb2e8273-7b61-4113-bfc8-f7ccc607c811
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 848e82741954ab24941d5d519699292727ca25d6
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "81301803"
---
# <a name="sqlremovedsnfromini-function"></a>Функция SQLRemoveDSNFromIni
**Соответствия**  
 Введенная версия: ODBC 1,0  
  
 **Сводка**  
 **Склремоведснфромини** удаляет источник данных из сведений о системе.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
  
BOOL SQLRemoveDSNFromIni(  
     LPCSTR   lpszDSN);  
```  
  
## <a name="arguments"></a>Аргументы  
 *лпсздсн*  
 Входной Имя удаляемого источника данных.  
  
## <a name="returns"></a>Результаты  
 Функция возвращает значение TRUE, если удаляется источник данных, или источник данных не находится в файле ODBC. ini. Он возвращает значение FALSE, если не удается удалить источник данных.  
  
## <a name="diagnostics"></a>Диагностика  
 Когда **склремоведснфромини** возвращает значение false, связанное * \*значение пферроркоде* может быть получено путем вызова **склинсталлереррор**. В следующей таблице перечислены значения * \*пферроркоде* , которые могут быть возвращены **склинсталлереррор** , и объясняется каждый из них в контексте этой функции.  
  
|*\*пферроркоде*|Error|Описание|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_GENERAL_ERR|Общая ошибка установщика|Произошла ошибка, для которой не возникала конкретная ошибка установщика.|  
|ODBC_ERROR_INVALID_DSN|Недопустимое имя DSN|Недопустимый аргумент *лпсздсн* .|  
|ODBC_ERROR_REQUEST_FAILED|Не удалось выполнить запрос|Установщику не удалось удалить из реестра сведения о DSN.|  
|ODBC_ERROR_OUT_OF_MEM|Недостаточно памяти|Установщику не удалось выполнить функцию из-за нехватки памяти.|  
  
## <a name="comments"></a>Комментарии  
 **Склремоведснфромини** удаляет имя источника данных из раздела [источники данных ODBC] сведений о системе. Он также удаляет раздел спецификации источника данных из сведений о системе.  
  
 Эта функция должна вызываться только из библиотеки установки драйвера.  
  
## <a name="related-functions"></a>Связанные функции  
  
|Сведения о|См.|  
|---------------------------|---------|  
|Добавление, изменение или удаление источника данных|[ConfigDSN](../../../odbc/reference/syntax/configdsn-function.md)|  
|Добавление, изменение или удаление источника данных|[SQLConfigDataSource](../../../odbc/reference/syntax/sqlconfigdatasource-function.md)|  
|Удаление источника данных по умолчанию|[склремоведефаултдатасаурце](../../../odbc/reference/syntax/sqlremovedefaultdatasource-function.md)|  
|Добавление имени источника данных в сведения о системе|[склвритедснтоини](../../../odbc/reference/syntax/sqlwritedsntoini-function.md)|
