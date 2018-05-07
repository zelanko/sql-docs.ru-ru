---
title: Функция SQLGetInstalledDrivers | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
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
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 6b45bd7c06b5c8e87c13fd8d9e956072ffebe858
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="sqlgetinstalleddrivers-function"></a>Функция SQLGetInstalledDrivers
**Соответствия**  
 Версии появился: ODBC 1.0  
  
 **Сводка**  
 **SQLGetInstalledDrivers** считывает в разделе [драйверов ODBC], информация о системе и возвращает список описаний установленных драйверов.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
BOOL SQLGetInstalledDrivers(  
     LPSTR   lpszBuf,  
     WORD    cbBufMax,  
     WORD *  pcbBufOut);  
```  
  
## <a name="arguments"></a>Аргументы  
 *lpszBuf*  
 [Выход] Список описаний установленных драйверов. Сведения о структуре списка см. в разделе «Комментарии».  
  
 *cbBufMax*  
 [Вход] Длина *lpszBuf*.  
  
 *pcbBufOut*  
 [Выход] Общее число байтов (за исключением байтов конечное значение null) возвращается в *lpszBuf*. Если количество байтов, доступных для возврата больше или равно *cbBufMax*, список описаний драйвер в *lpszBuf* усекается до *cbBufMax* минус знак завершения NULL. *PcbBufOut* аргумент может быть пустой указатель.  
  
## <a name="returns"></a>Возвращает  
 Функция возвращает значение TRUE, если он прошел успешно, FALSE в случае неудачи.  
  
## <a name="diagnostics"></a>Диагностика  
 Когда **SQLGetInstalledDrivers** возвращает значение FALSE, связанный с ним  *\*pfErrorCode* значение можно получить путем вызова **SQLInstallerError**. В следующей таблице перечислены  *\*pfErrorCode* значения, которые могут быть возвращены **SQLInstallerError** и описание каждого из них в контексте этой функции.  
  
|*\*pfErrorCode*|Ошибка|Описание|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_GENERAL_ERR|Установщик Общие ошибки|Произошла ошибка для которого нет ошибок определенного установщика.|  
|ODBC_ERROR_INVALID_BUFF_LEN|Недопустимый буфер длины|*LpszBuf* аргумент имеет значение NULL или недопустим, или *cbBufMax* аргумент был меньше или равно 0.|  
|ODBC_ERROR_COMPONENT_NOT_FOUND|Компонент не найден в реестре|Программе установки не удалось найти раздел [ODBC Drivers] в реестре.|  
|ODBC_ERROR_OUT_OF_MEM|Недостаточно памяти|Программе установки не удалось выполнить функцию из-за нехватки памяти.|  
  
## <a name="comments"></a>Комментарии  
 Каждое описание драйвер заканчивается нулевым байтом, и завершается нулевым байтом весь список. (То есть две пустые байты отмечающий конец списка.) Если выделенный буфер недостаточно велик для хранения списка в целом, список будет усечен без ошибок. Возвращается сообщение об ошибке, если указатель null передается в качестве *lpszBuf*.  
  
## <a name="related-functions"></a>Связанные функции  
  
|Сведения о|См.|  
|---------------------------|---------|  
|Возврат описания драйверов и атрибуты|[SQLDrivers](../../../odbc/reference/syntax/sqldrivers-function.md)|
