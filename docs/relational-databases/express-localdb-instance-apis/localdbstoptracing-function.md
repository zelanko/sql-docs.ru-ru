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
ms.openlocfilehash: 5d26d5a7dd54adaae212a840e3183ff3f098d845
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85765181"
---
# <a name="localdbstoptracing-function"></a>Функция LocalDBStopTracing
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  Отключает трассировку вызовов API для всех экземпляров SQL Server Express LocalDB, принадлежащих текущему пользователю Windows.  
  
 **Файл заголовка:** sqlncli.h  
  
## <a name="syntax"></a>Синтаксис  
  
```  
HRESULT LocalDBStopTracing();  
```  
  
## <a name="returns"></a>Возвращаемое значение  
 S_OK  
 Функция выполнена успешно.  
  
 [LOCALDB_ERROR_INTERNAL_ERROR](../../relational-databases/express-localdb-error-messages/localdb-error-internal-error.md)  
 Произошла непредвиденная ошибка. Подробные сведения см. в журнале событий.  
  
## <a name="remarks"></a>Примечания  
 Образец кода, использующего API LocalDB, см. в разделе [SQL Server Express LocalDB Reference](../../relational-databases/sql-server-express-localdb-reference.md)  
  
## <a name="see-also"></a>См. также  
 [Заголовок и сведения о версии SQL Server Express LocalDB](../../relational-databases/express-localdb-instance-apis/sql-server-express-localdb-header-and-version-information.md)  
  
  
