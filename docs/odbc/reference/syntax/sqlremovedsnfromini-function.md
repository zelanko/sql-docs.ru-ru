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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 4cc83a8cafffc9b5d1166df76d91ce4c63f0b858
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68024528"
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
  
## <a name="returns"></a>Возвращает  
 Функция возвращает значение TRUE, если удаляется источник данных, или источник данных не находится в файле ODBC. ini. Он возвращает значение FALSE, если не удается удалить источник данных.  
  
## <a name="diagnostics"></a>Диагностика  
 Когда **склремоведснфромини** возвращает значение false, связанное * \*значение пферроркоде* может быть получено путем вызова **склинсталлереррор**. В следующей таблице перечислены значения * \*пферроркоде* , которые могут быть возвращены **склинсталлереррор** , и объясняется каждый из них в контексте этой функции.  
  
|*\*пферроркоде*|Ошибка|Description|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_GENERAL_ERR|Общая ошибка установщика|Произошла ошибка, для которой не возникала конкретная ошибка установщика.|  
|ODBC_ERROR_INVALID_DSN|Недопустимое имя DSN|Недопустимый аргумент *лпсздсн* .|  
|ODBC_ERROR_REQUEST_FAILED|Сбой запроса|Установщику не удалось удалить из реестра сведения о DSN.|  
|ODBC_ERROR_OUT_OF_MEM|Недостаточно памяти|Установщику не удалось выполнить функцию из-за нехватки памяти.|  
  
## <a name="comments"></a>Комментарии  
 **Склремоведснфромини** удаляет имя источника данных из раздела [источники данных ODBC] сведений о системе. Он также удаляет раздел спецификации источника данных из сведений о системе.  
  
 Эта функция должна вызываться только из библиотеки установки драйвера.  
  
## <a name="related-functions"></a>Связанные функции  
  
|Тема|См. следующие документы.|  
|---------------------------|---------|  
|Добавление, изменение или удаление источника данных|[ConfigDSN](../../../odbc/reference/syntax/configdsn-function.md)|  
|Добавление, изменение или удаление источника данных|[SQLConfigDataSource](../../../odbc/reference/syntax/sqlconfigdatasource-function.md)|  
|Удаление источника данных по умолчанию|[склремоведефаултдатасаурце](../../../odbc/reference/syntax/sqlremovedefaultdatasource-function.md)|  
|Добавление имени источника данных в сведения о системе|[склвритедснтоини](../../../odbc/reference/syntax/sqlwritedsntoini-function.md)|
