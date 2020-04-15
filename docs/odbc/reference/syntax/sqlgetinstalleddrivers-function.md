---
title: Функция S'LGetInstalledDrivers (ru) Документы Майкрософт
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 24793473bf4f25253ac11673df852d10cfb2c558
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81303331"
---
# <a name="sqlgetinstalleddrivers-function"></a>Функция SQLGetInstalledDrivers
**Соответствия**  
 Представлена версия: ODBC 1.0  
  
 **Сводка**  
 **SLGetInstalledDrivers** читает раздел «OdBC Drivers» в системе и возвращает список описаний установленных драйверов.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
  
BOOL SQLGetInstalledDrivers(  
     LPSTR   lpszBuf,  
     WORD    cbBufMax,  
     WORD *  pcbBufOut);  
```  
  
## <a name="arguments"></a>Аргументы  
 *lpszBuf*  
 (Выход) Список описаний установленных драйверов. Для получения информации о структуре списка см.  
  
 *cbBufMax*  
 (Вход) Длина *lpszBuf*.  
  
 *pcbBufOut*  
 (Выход) Общее количество байтов (за исключением байт-навили) возвращается в *lpszBuf*. Если количество байтов, доступных для возврата, больше или равно *cbBufMax,* список описаний драйверов в *lpszBuf* усечен *до cbBufMax* минус символ нулевого прекращения. Аргумент *pcbBufOut* может быть нулевым указателем.  
  
## <a name="returns"></a>Результаты  
 Функция возвращает TRUE, если она успешна, FALSE, если она не удается.  
  
## <a name="diagnostics"></a>Диагностика  
 Когда **S'LGetInstalledDrivers** возвращает FALSE, связанное * \*значение pfErrorCode* можно получить, позвонив по **телефону S'LInstallerError.** В следующей таблице перечислены * \*значения pfErrorCode,* которые могут быть возвращены **S'LInstallerError,** и приведены в изъяны каждое из них в контексте этой функции.  
  
|*\*pfErrorCode*|Error|Описание|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_GENERAL_ERR|Общая ошибка установки|Произошла ошибка, для которой не было конкретной ошибки установки.|  
|ODBC_ERROR_INVALID_BUFF_LEN|Недействительная длина буфера|*LpszBuf* аргумент был null или недействительным, или *аргумент cbBufMax* был меньше, чем или равна 0.|  
|ODBC_ERROR_COMPONENT_NOT_FOUND|Компонент не найден в реестре|Установщик не смог найти раздел «Водители ODBC» в реестре.|  
|ODBC_ERROR_OUT_OF_MEM|Недостаточно памяти|Установщик не мог выполнить функцию из-за отсутствия памяти.|  
  
## <a name="comments"></a>Комментарии  
 Каждое описание драйвера прекращается с нулевым байтом, и весь список завершается нулевым байтом. (То есть, два нулевых байта отмечают конец списка.) Если выделенный буфер недостаточно велик, чтобы удерживать весь список, список усечен без ошибок. Ошибка возвращается, если нулевая указка передается в качестве *lpszBuf*.  
  
## <a name="related-functions"></a>Связанные функции  
  
|Сведения о|См.|  
|---------------------------|---------|  
|Возвращение описания и атрибутики драйвера|[SQLDrivers](../../../odbc/reference/syntax/sqldrivers-function.md)|
