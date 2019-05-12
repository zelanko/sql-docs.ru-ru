---
title: Функция SQLGetInstalledDrivers | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLGetInstalledDrivers
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLGetInstalledDrivers
helpviewer_keywords:
- SQLGetInstalledDrivers function [ODBC]
ms.assetid: a1983a2e-0edf-422e-bd1b-ec5db40a34bc
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 0ff675a184ea0804988972ef10e9a383cdd45230
ms.sourcegitcommit: 7a3243c45830cb3f49a7fa71c2991a9454fd6f5a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/11/2019
ms.locfileid: "65537206"
---
# <a name="sqlgetinstalleddrivers-function"></a>Функция SQLGetInstalledDrivers
**Соответствие стандартам**  
 Представленные версии: ODBC 1.0  
  
 **Сводка**  
 **SQLGetInstalledDrivers** изучает раздел [ODBC Drivers] Информация о системе и возвращает список описаний установленных драйверов.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
  
BOOL SQLGetInstalledDrivers(  
     LPSTR   lpszBuf,  
     WORD    cbBufMax,  
     WORD *  pcbBufOut);  
```  
  
## <a name="arguments"></a>Аргументы  
 *lpszBuf*  
 [Выход] Список описаний установленных драйверов. Сведения о структуре списка см. в разделе «Примечания».  
  
 *cbBufMax*  
 [Вход] Длина *lpszBuf*.  
  
 *pcbBufOut*  
 [Выход] Общее число байтов (за исключением байтов конечное значение null) возвращаются в *lpszBuf*. Если количество байтов, доступных для возврата больше или равно *cbBufMax*, список описаний драйвера в *lpszBuf* усекается до *cbBufMax* минус символ завершения NULL. *PcbBufOut* аргументом может быть пустым указателем.  
  
## <a name="returns"></a>Возвращает  
 Функция возвращает значение TRUE при успешном выполнении, FALSE в случае неудачи.  
  
## <a name="diagnostics"></a>Диагностика  
 Когда **SQLGetInstalledDrivers** возвращает значение FALSE, связанным  *\*pfErrorCode* значение можно получить, вызвав **SQLInstallerError**. В следующей таблице перечислены  *\*pfErrorCode* значения, которые могут быть возвращены **SQLInstallerError** и объясняется каждый из них в контексте этой функции.  
  
|*\*pfErrorCode*|Ошибка|Описание|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_GENERAL_ERR|Ошибки общие установщика|Произошла ошибка для которой нет ошибок определенных установщика.|  
|ODBC_ERROR_INVALID_BUFF_LEN|Недопустимый буфер длины|*LpszBuf* аргумент имел значение NULL или недопустимо, или *cbBufMax* аргумент был меньше или равно 0.|  
|ODBC_ERROR_COMPONENT_NOT_FOUND|Компонент не найден в реестре|Программа установки не удалось найти в разделе [ODBC Drivers] в реестре.|  
|ODBC_ERROR_OUT_OF_MEM|Недостаточно памяти|Программа установки не удалось выполнить функцию из-за нехватки памяти.|  
  
## <a name="comments"></a>Комментарии  
 Каждое описание драйвера заканчивается нулевым байтом, а весь список заканчивается нулевым байтом. (То есть две пустые байты обозначения конца списка.) Если выделенный буфер не является достаточно велик для хранения по всему списку, списке усекаются без ошибок. Ошибка возвращается в том случае, если указатель null передается как *lpszBuf*.  
  
## <a name="related-functions"></a>Связанные функции  
  
|Сведения о|См.|  
|---------------------------|---------|  
|Возврат описания драйверов и атрибуты|[SQLDrivers](../../../odbc/reference/syntax/sqldrivers-function.md)|
