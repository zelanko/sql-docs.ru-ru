---
title: Функция LocalDBStopTracing | Документация Майкрософт
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
apiname:
- LocalDBStopTracing
apilocation:
- sqluserinstance.dll
apitype: DLLExport
ms.assetid: 1d50e040-8602-4ffa-be8f-b8633fdfa7ff
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: e35b0c9b806b435a4a98a319180801094068caf1
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68022042"
---
# <a name="localdbstoptracing-function"></a>Функция LocalDBStopTracing
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Отключает трассировку вызовов API для всех экземпляров SQL Server Express LocalDB, принадлежащих текущему пользователю Windows.  
  
 **Заголовочный файл:** sqlncli. h  
  
## <a name="syntax"></a>Синтаксис  
  
```  
HRESULT LocalDBStopTracing();  
```  
  
## <a name="returns"></a>Возвращает  
 S_OK  
 Функция выполнена успешно.  
  
 [LOCALDB_ERROR_INTERNAL_ERROR](../../relational-databases/express-localdb-error-messages/localdb-error-internal-error.md)  
 Произошла непредвиденная ошибка. Подробные сведения см. в журнале событий.  
  
## <a name="remarks"></a>Remarks  
 Образец кода, использующего API LocalDB, см. в разделе [SQL Server Express LocalDB Reference](../../relational-databases/sql-server-express-localdb-reference.md)  
  
## <a name="see-also"></a>См. также:  
 [Заголовок и сведения о версии SQL Server Express LocalDB](../../relational-databases/express-localdb-instance-apis/sql-server-express-localdb-header-and-version-information.md)  
  
  
