---
title: Функция LocalDBGetInstances | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
apiname:
- LocalDBGetInstances
apilocation:
- sqluserinstance.dll
apitype: DLLExport
ms.assetid: f95a9980-8bc0-426c-8aa1-e2660b6784cf
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 04554c7aa9f891aab414ae5ae77f3c92bb86ac4b
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68036048"
---
# <a name="localdbgetinstances-function"></a>Функция LocalDBGetInstances
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Возвращает все экземпляры SQL Server Express LocalDB с данной версией.  
  
 **Файл заголовка:** sqlncli.h  
  
## <a name="syntax"></a>Синтаксис  
  
```  
#define MAX_LOCALDB_INSTANCE_NAME_LENGTH 128typedef WCHAR TLocalDBInstanceName[MAX_LOCALDB_INSTANCE_NAME_LENGTH + 1];typedef TLocalDBInstanceName* PTLocalDBInstanceName;  
HRESULT LocalDBGetInstances(  
           PTLocalDBInstanceName pInstanceNames,  
           LPDWORD lpdwNumberOfInstances  
);  
```  
  
## <a name="parameters"></a>Параметры  
 *pInstanceNames*  
 [Выход] Когда эта функция возвращает значение, содержащий имена и именованные и экземпляров LocalDB на рабочей станции пользователя по умолчанию.  
  
 *lpdwNumberOfInstances*  
 [Вход/Выход] На входе содержит число ячеек для имен экземпляров в буфере *pInstanceNames* . На выходе содержит количество экземпляров LocalDB, найденных на рабочей станции пользователя.  
  
## <a name="returns"></a>Возвращает  
 S_OK  
 Функция выполнена успешно.  
  
 [LOCALDB_ERROR_NOT_INSTALLED](../../relational-databases/express-localdb-error-messages/localdb-error-not-installed.md)  
 Компонент SQL Server Express LocalDB не установлен на компьютере.  
  
 [LOCALDB_ERROR_INVALID_PARAMETER](../../relational-databases/express-localdb-error-messages/localdb-error-invalid-parameter.md)  
 Один или несколько указанных входных параметров недопустимы.  
  
 [LOCALDB_ERROR_INSUFFICIENT_BUFFER](../../relational-databases/express-localdb-error-messages/localdb-error-insufficient-buffer.md)  
 Размер входного буфера является недостаточным, а усечение не было запрошено.  
  
 [LOCALDB_ERROR_INSTANCE_FOLDER_PATH_TOO_LONG](../../relational-databases/express-localdb-error-messages/localdb-error-instance-folder-path-too-long.md)  
 Длина пути к месту хранения экземпляра больше MAX_PATH.  
  
 [LOCALDB_ERROR_CANNOT_ACCESS_INSTANCE_REGISTRY](../../relational-databases/express-localdb-error-messages/localdb-error-cannot-access-instance-registry.md)  
 Не удалось получить доступ к реестру экземпляра.  
  
 [LOCALDB_ERROR_INSTANCE_CONFIGURATION_CORRUPT](../../relational-databases/express-localdb-error-messages/localdb-error-instance-configuration-corrupt.md)  
 Конфигурация экземпляра повреждена.  
  
 [LOCALDB_ERROR_INTERNAL_ERROR](../../relational-databases/express-localdb-error-messages/localdb-error-internal-error.md)  
 Произошла непредвиденная ошибка. Подробные сведения см. в журнале событий.  
  
## <a name="remarks"></a>Примечания  
 Образец кода, использующего API LocalDB, см. в разделе [SQL Server Express LocalDB Reference](../../relational-databases/sql-server-express-localdb-reference.md)  
  
## <a name="see-also"></a>См. также  
 [Заголовок и сведения о версии SQL Server Express LocalDB](../../relational-databases/express-localdb-instance-apis/sql-server-express-localdb-header-and-version-information.md)  
  
  
