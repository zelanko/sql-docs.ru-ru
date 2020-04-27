---
title: Функция LocalDBGetInstanceInfo | Документация Майкрософт
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
api_name:
- LocalDBGetInstanceInfo
api_location:
- sqluserinstance.dll
topic_type:
- apiref
ms.assetid: 231706f5-26c6-42eb-ab47-315df6b8f824
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 889e5eee49363c71a18808e7c71434110241bc84
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "63130525"
---
# <a name="localdbgetinstanceinfo-function"></a>Функция LocalDBGetInstanceInfo
  Возвращает сведения об указанном экземпляре среды выполнения экземпляра SQL Server Express LocalDB, в частности существует ли этот экземпляр, версия используемой им LocalDB, запущен ли экземпляр и т. п.  
  
 Эти сведения возвращаются в `struct` именованном **локалдбинстанцеинфо**, который имеет следующее определение.  
  
```  
typedef struct _LocalDBInstanceInfo  
{  
      // Contains the size of the LocalDBInstanceInfo struct  
      DWORD  cbLocalDBInstanceInfoSize;  
  
      // Holds the instance name  
      TLocalDBInstanceNamewszInstanceName;  
  
      // TRUE if the instance files exist on disk, FALSE otherwise  
      BOOL   bExists;  
  
      // TRUE if the instance configuration registry is corrupted, FALSE otherwise  
      BOOLbConfigurationCorrupted;  
  
      // TRUE if the instance is running at the moment, FALSE otherwise  
      BOOL   bIsRunning;  
  
      // Holds the LocalDB version for the instance in the format: major.minor.build.revision  
      DWORD  dwMajor;  
      DWORD  dwMinor;  
      DWORD  dwBuild;  
      DWORD  dwRevision;  
  
      // Holds the date and time when the instance was started for the last time  
      FILETIME ftLastStartUTC;  
  
      // Holds the name of the TDS named pipe to connect to the instance  
      WCHARwszConnection;  
  
      // TRUE if the instance is shared, FALSE otherwise  
      BOOLbIsShared;  
  
      // Holds the shared name for the instance (if the instance is shared)  
      TLocalDBInstanceNamewszSharedInstanceName;  
  
      // Holds the SID of the instance owner (if the instance is shared)  
      WCHARwszOwnerSID;   
  
      // TRUE if the instance is Automatic, FALSE otherwise  
      BOOLbIsAutomatic;  
} LocalDBInstanceInfo;  
  
```  
  
 **Файл заголовка:** sqlncli.h  
  
## <a name="syntax"></a>Синтаксис  
  
```  
HRESULT LocalDBGetInstanceInfo(  
           PCWSTR wszInstanceName,  
           PLocalDBInstanceInfo pInstanceInfo,  
           DWORD dwInstanceInfoSize   
);  
```  
  
## <a name="parameters"></a>Параметры  
 *всзинстанценаме*  
 [Вход] Имя экземпляра.  
  
 *пинстанцеинфо*  
 [Выход] Буфер для сохранения сведений об экземпляре LocalDB.  
  
 *двинстанцеинфосизе*  
 Входной Содержит размер буфера *инстанцеинфо* .  
  
## <a name="returns"></a>Результаты  
 S_OK  
 Функция выполнена успешно.  
  
 [LOCALDB_ERROR_NOT_INSTALLED](../express-localdb-error-messages/localdb-error-not-installed.md)  
 Компонент SQL Server Express LocalDB не установлен на компьютере.  
  
 [LOCALDB_ERROR_INVALID_PARAMETER](../express-localdb-error-messages/localdb-error-invalid-parameter.md)  
 Один или несколько указанных входных параметров недопустимы.  
  
 [LOCALDB_ERROR_INVALID_INSTANCE_NAME](../express-localdb-error-messages/localdb-error-invalid-instance-name.md)  
 Указанное имя экземпляра недопустимо.  
  
 [LOCALDB_ERROR_UNKNOWN_INSTANCE](../express-localdb-error-messages/localdb-error-unknown-instance.md)  
 Экземпляр не существует.  
  
 [LOCALDB_ERROR_INSTANCE_FOLDER_PATH_TOO_LONG](../express-localdb-error-messages/localdb-error-instance-folder-path-too-long.md)  
 Длина пути к месту хранения экземпляра больше MAX_PATH.  
  
 [LOCALDB_ERROR_CANNOT_ACCESS_INSTANCE_FOLDER](../express-localdb-error-messages/localdb-error-cannot-access-instance-folder.md)  
 Не удалось получить доступ к папке экземпляра.  
  
 [LOCALDB_ERROR_CANNOT_ACCESS_INSTANCE_REGISTRY](../express-localdb-error-messages/localdb-error-cannot-access-instance-registry.md)  
 Не удалось получить доступ к реестру экземпляра.  
  
 [LOCALDB_ERROR_INSTANCE_CONFIGURATION_CORRUPT](../express-localdb-error-messages/localdb-error-instance-configuration-corrupt.md)  
 Конфигурация экземпляра повреждена.  
  
 [LOCALDB_ERROR_INTERNAL_ERROR](../express-localdb-error-messages/localdb-error-internal-error.md)  
 Произошла непредвиденная ошибка. Подробные сведения см. в журнале событий.  
  
## <a name="details"></a>Подробности  
 Смысл в поведении аргумента `struct` size (*лпинстанцеинфосизе*) заключается в том, чтобы позволить API возвращать различные версии **локалдбинстанцеинфострукт**, эффективно обеспечивая прямую и обратную совместимость.  
  
 Если аргумент `struct` size (*лпинстанцеинфосизе*) соответствует размеру известной версии **локалдбинстанцеинфострукт**, возвращается эта версия `struct` . В противном случае возвращается значение LOCALDB_ERROR_INVALID_PARAMETER.  
  
 Типичный пример использования API **LocalDBGetInstanceInfo** выглядит следующим образом:  
  
```  
LocalDBInstanceInfo ii;  
LocalDBInstanceInfo(L"Test", &ii, sizeof(LocalDBInstanceInfo));  
  
```  
  
 Образец кода, использующего API LocalDB, см. в разделе [SQL Server Express LocalDB Reference](../sql-server-express-localdb-reference.md)  
  
## <a name="see-also"></a>См. также  
 [Заголовок и сведения о версии SQL Server Express LocalDB](sql-server-express-localdb-header-and-version-information.md)  
  
  
