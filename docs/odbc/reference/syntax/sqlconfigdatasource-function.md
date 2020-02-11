---
title: Функция SQLConfigDataSource | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLConfigDataSource
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLConfigDataSource
helpviewer_keywords:
- SQLConfigDataSource function [ODBC]
ms.assetid: f8d6e342-c010-434e-b1cd-f5371fb50a14
author: MightyPen
ms.author: genemi
ms.openlocfilehash: e7706d3a7dd05273b4608d49211a6eaab8927f2a
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68118610"
---
# <a name="sqlconfigdatasource-function"></a>SQLConfigDataSource, функция
**Соответствия**  
 Введенная версия: ODBC 1,0  
  
 **Сводка**  
 **SQLConfigDataSource** добавляет, изменяет или удаляет источники данных.  
  
 Функциональность **SQLConfigDataSource** также можно получить с помощью [одбкконф. EXE](../../../odbc/odbcconf-exe.md).  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
  
BOOL SQLConfigDataSource(  
     HWND     hwndParent,  
     WORD     fRequest,  
     LPCSTR   lpszDriver,  
     LPCSTR   lpszAttributes);  
```  
  
## <a name="arguments"></a>Аргументы  
 *хвндпарент*  
 Входной Маркер родительского окна. Функция не отображает никакие диалоговые окна, если этот маркер имеет значение null.  
  
 *фрекуест*  
 Входной Тип запроса. Аргумент *фрекуест* должен содержать одно из следующих значений:  
  
 ODBC_ADD_DSN. Добавьте новый источник данных пользователя.  
  
 ODBC_CONFIG_DSN: Настройка (изменение) существующего источника данных пользователя.  
  
 ODBC_REMOVE_DSN: удалите существующий источник данных пользователя.  
  
 ODBC_ADD_SYS_DSN. Добавьте новый системный источник данных.  
  
 ODBC_CONFIG_SYS_DSN: измените существующий системный источник данных.  
  
 ODBC_REMOVE_SYS_DSN: удалите существующий системный источник данных.  
  
 ODBC_REMOVE_DEFAULT_DSN: удалите раздел "Спецификация источника данных по умолчанию" из сведений о системе. (Он также удаляет раздел спецификации драйвера по умолчанию из записи Odbcinst. ini в разделе сведения о системе. Эта *фрекуест* выполняет ту же функцию, что и устаревшая функция **склремоведефаултдатасаурце** .) Если указан этот параметр, все остальные параметры в вызове **SQLConfigDataSource** должны быть равны NULL. Если они не равны NULL, они будут пропущены.  
  
 *лпсздривер*  
 Входной Описание драйвера (обычно имя связанной СУБД), представленное пользователям вместо физического имени драйвера.  
  
 *лпсзаттрибутес*  
 Входной Список атрибутов в виде пар «ключевое слово-значение» с удвоенным нулем. Дополнительные сведения см. в разделе [ConfigDSN](../../../odbc/reference/syntax/configdsn-function.md).  
  
## <a name="returns"></a>Возвращает  
 Функция возвращает TRUE, если она успешна, и FALSE в случае сбоя. Если при вызове этой функции в системной информации не существует записи, функция возвращает значение FALSE.  
  
## <a name="diagnostics"></a>Диагностика  
 Когда **SQLConfigDataSource** возвращает значение false, связанное * \*значение пферроркоде* может быть получено путем вызова **склинсталлереррор**. В следующей таблице перечислены значения * \*пферроркоде* , которые могут быть возвращены **склинсталлереррор** , и объясняется каждый из них в контексте этой функции.  
  
|*\*пферроркоде*|Ошибка|Description|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_GENERAL_ERR|Общая ошибка установщика|Произошла ошибка, для которой не возникала конкретная ошибка установщика.|  
|ODBC_ERROR_INVALID_HWND|Недопустимый маркер окна|Аргумент *хвндпарент* недопустим или имеет значение null.|  
|ODBC_ERROR_INVALID_REQUEST_TYPE|Недопустимый тип запроса|Аргумент *фрекуест* не является одним из следующих:<br /><br /> ODBC_ADD_DSN ODBC_CONFIG_DSN ODBC_REMOVE_DSN ODBC_ADD_SYS_DSN ODBC_CONFIG_SYS_DSN ODBC_REMOVE_SYS_DSN ODBC_REMOVE_DEFAULT_DSN|  
|ODBC_ERROR_INVALID_NAME|Недопустимое имя драйвера или транслятора|Недопустимый аргумент *лпсздривер* . Не удалось найти его в реестре.|  
|ODBC_ERROR_INVALID_KEYWORD_VALUE|Недопустимые пары "ключевое слово-значение"|Аргумент *лпсзаттрибутес* содержал синтаксическую ошибку.|  
|ODBC_ERROR_REQUEST_FAILED|Сбой *запроса*|Установщику не удалось выполнить операцию, запрошенную аргументом *фрекуест* . Сбой вызова **ConfigDSN** .|  
|ODBC_ERROR_LOAD_LIBRARY_FAILED|Не удалось загрузить драйвер или библиотеку установки переводчика|Не удалось загрузить библиотеку установки драйверов.|  
|ODBC_ERROR_OUT_OF_MEM|Недостаточно памяти|Установщику не удалось выполнить функцию из-за нехватки памяти.|  
  
## <a name="comments"></a>Комментарии  
 **SQLConfigDataSource** использует значение *лпсздривер* для чтения полного пути к библиотеке DLL установки драйвера из сведений о системе. Он загружает библиотеку DLL и вызывает **ConfigDSN** с теми же аргументами, которые были переданы в нее.  
  
 **SQLConfigDataSource** возвращает значение false, если не удается найти или загрузить библиотеку DLL установки или если пользователь отменяет диалоговое окно. В противном случае возвращается состояние, полученное от **ConfigDSN**.  
  
 **SQLConfigDataSource** СОПОСТАВЛЯЕТ системный DSN *Фрекуест*s с пользовательским dsn *фрекуест*s (ODBC_ADD_SYS_DSN для ODBC_ADD_DSN, ODBC_CONFIG_SYS_DSN ODBC_CONFIG_DSN и ODBC_REMOVE_SYS_DSN в ODBC_REMOVE_DSN). Чтобы отличать пользовательские и системные имена DSN, **SQLConfigDataSource** устанавливает режим конфигурации установщика в соответствии со следующей таблицей. Перед возвратом **SQLConfigDataSource** режим конфигурации сбрасывается в босдсн. **ConfigDSN** (реализованные драйверами) должны вызывать **склвритедснтоини** и **склвритеприватепрофилестринг** для поддержки системного имени DSN. Дополнительные сведения см. в разделе [функция ConfigDSN](../../../odbc/reference/syntax/configdsn-function.md).  
  
|*фрекуест*|Режим конфигурации|  
|----------------|------------------------|  
|ODBC_ADD_DSN|USERDSN_ONLY|  
|ODBC_CONFIG_DSN|USERDSN_ONLY|  
|ODBC_REMOVE_DSN|USERDSN_ONLY|  
|ODBC_ADD_SYS_DSN|SYSTEMDSN_ONLY|  
|ODBC_CONFIG_SYS_DSN|SYSTEMDSN_ONLY|  
|ODBC_REMOVE_SYS_DSN|SYSTEMDSN_ONLY|  
  
## <a name="related-functions"></a>Связанные функции  
  
|Тема|См. следующие документы.|  
|---------------------------|---------|  
|Добавление, изменение или удаление источника данных|[ConfigDSN](../../../odbc/reference/syntax/configdsn-function.md) (в библиотеке DLL установки)|  
|Удаление имени источника данных из сведений о системе|[склремоведснфромини](../../../odbc/reference/syntax/sqlremovedsnfromini-function.md)|  
|Добавление имени источника данных в сведения о системе|[склвритедснтоини](../../../odbc/reference/syntax/sqlwritedsntoini-function.md)|
