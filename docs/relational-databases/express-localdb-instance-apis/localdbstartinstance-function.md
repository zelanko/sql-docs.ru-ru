---
title: Функция LocalDBStartInstance | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
apiname:
- LocalDBStartInstance
apilocation:
- sqluserinstance.dll
apitype: DLLExport
ms.assetid: cb325f5d-10ee-4a56-ba28-db0074ab3926
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: b06364adefd62b4267d43bac50d79f8f1d37958a
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68022089"
---
# <a name="localdbstartinstance-function"></a>Функция LocalDBStartInstance
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Запускает экземпляр SQL Server Express LocalDB.  
  
 **Файл заголовка:** sqlncli.h  
  
## <a name="syntax"></a>Синтаксис  
  
```  
HRESULT LocalDBStartInstance(  
           PCWSTR pInstanceName,  
           DWORD dwFlags,   
           LPWSTR wszSqlConnection,   
           LPDWORD lpcchSqlConnection   
);  
```  
  
## <a name="parameters"></a>Параметры  
 *pInstanceName*  
 [Вход] Имя запускаемого экземпляра LocalDB.  
  
 *dwFlags*  
 [Вход] Зарезервировано для использования в будущем. В настоящее время должно быть равным 0.  
  
 *wszSqlConnection*  
 [Выход] Буфер для хранения строки подключения к экземпляру LocalDB.  
  
 *lpcchSqlConnection*  
 [Вход/выход] На входе содержит размер буфера *wszSqlConnection* в символах, включая конечные значения NULL. На выходе, если указан недостаточный размер буфера, содержит требуемый размер буфера в символах, включая любые конечные символы NULL.  
  
## <a name="returns"></a>Возвращает  
 S_OK  
 Функция выполнена успешно.  
  
 [LOCALDB_ERROR_NOT_INSTALLED](../../relational-databases/express-localdb-error-messages/localdb-error-not-installed.md)  
 Компонент SQL Server Express LocalDB не установлен на компьютере.  
  
 [LOCALDB_ERROR_INVALID_PARAMETER](../../relational-databases/express-localdb-error-messages/localdb-error-invalid-parameter.md)  
 Один или несколько указанных входных параметров недопустимы.  
  
 [LOCALDB_ERROR_INVALID_INSTANCE_NAME](../../relational-databases/express-localdb-error-messages/localdb-error-invalid-instance-name.md)  
 Указанное имя экземпляра недопустимо.  
  
 [LOCALDB_ERROR_UNKNOWN_INSTANCE](../../relational-databases/express-localdb-error-messages/localdb-error-unknown-instance.md)  
 Экземпляр не существует.  
  
 [LOCALDB_ERROR_INSUFFICIENT_BUFFER](../../relational-databases/express-localdb-error-messages/localdb-error-insufficient-buffer.md)  
 Указан недостаточный размер буфера *wszSqlConnection* .  
  
 [LOCALDB_ERROR_WAIT_TIMEOUT](../../relational-databases/express-localdb-error-messages/localdb-error-wait-timeout.md)  
 При попытке получения блокировок синхронизации истекло время ожидания.  
  
 [LOCALDB_ERROR_INSTANCE_FOLDER_PATH_TOO_LONG](../../relational-databases/express-localdb-error-messages/localdb-error-instance-folder-path-too-long.md)  
 Длина пути к месту хранения экземпляра больше MAX_PATH.  
  
 [LOCALDB_ERROR_CANNOT_GET_USER_PROFILE_FOLDER](../../relational-databases/express-localdb-error-messages/localdb-error-cannot-get-user-profile-folder.md)  
 Не удалось получить папку профиля пользователя.  
  
 [LOCALDB_ERROR_CANNOT_ACCESS_INSTANCE_FOLDER](../../relational-databases/express-localdb-error-messages/localdb-error-cannot-access-instance-folder.md)  
 Не удалось получить доступ к папке экземпляра.  
  
 [LOCALDB_ERROR_CANNOT_ACCESS_INSTANCE_REGISTRY](../../relational-databases/express-localdb-error-messages/localdb-error-cannot-access-instance-registry.md)  
 Не удалось получить доступ к реестру экземпляра.  
  
 [LOCALDB_ERROR_CANNOT_MODIFY_INSTANCE_REGISTRY](../../relational-databases/express-localdb-error-messages/localdb-error-cannot-modify-instance-registry.md)  
 Невозможно изменить реестр экземпляра.  
  
 [LOCALDB_ERROR_CANNOT_CREATE_SQL_PROCESS](../../relational-databases/express-localdb-error-messages/localdb-error-cannot-create-sql-process.md)  
 Не удалось создать процесс для SQL Server.  
  
 [LOCALDB_ERROR_SQL_SERVER_STARTUP_FAILED](../../relational-databases/express-localdb-error-messages/localdb-error-sql-server-startup-failed.md)  
 Был запущен процесс SQL Server, но запуск SQL Server завершился с ошибкой.  
  
 [LOCALDB_ERROR_INSTANCE_CONFIGURATION_CORRUPT](../../relational-databases/express-localdb-error-messages/localdb-error-instance-configuration-corrupt.md)  
 Конфигурация экземпляра была повреждена.  
  
 [LOCALDB_ERROR_AUTO_INSTANCE_CREATE_FAILED](../../relational-databases/express-localdb-error-messages/localdb-error-auto-instance-create-failed.md)  
 Невозможно создать автоматический экземпляр. Сведения об ошибке см. в журнале событий приложений Windows.  
  
 [LOCALDB_ERROR_INTERNAL_ERROR](../../relational-databases/express-localdb-error-messages/localdb-error-internal-error.md)  
 Произошла непредвиденная ошибка. Подробные сведения см. в журнале событий.  
  
## <a name="details"></a>Сведения  
 Аргумент буфера соединения (*wszSqlConnection*) и аргумент размера буфера соединения (*lpcchSqlConnection*) являются необязательными. В следующей таблице показаны варианты использования этих аргументов и их результаты.  
  
|Буфер|Размер буфера|Правильно|Action|  
|------------|-----------------|---------------|------------|  
|NULL|NULL|Пользователь хочет запустить экземпляр и не обязательно канала имя.|Запускает экземпляр (имя канала и необходимый размер буфера не возвращаются).|  
|NULL|Существует|Пользователь запрашивает размер выходного буфера. (При следующем вызове пользователь скорее всего запросит запуск).|Возвращает требуемый размер буфера (без запуска и возврата канала). Результат равен S_OK.|  
|Существует|NULL|Недопустимо; неверный вход.|Возвращаемый результат — LOCALDB_ERROR_INVALID_PARAMETER.|  
|Существует|Существует|Пользователь хочет запустить экземпляр и нуждается в имени канала для подключения к нему после запуска.|Проверяет размер буфера, запускает экземпляр и возвращает имя канала в буфере. <br />Аргумент размера буфера возвращает длину «server =» строки, не включая завершающие значения NULL.|  
  
 Образец кода, использующего API LocalDB, см. в разделе [SQL Server Express LocalDB Reference](../../relational-databases/sql-server-express-localdb-reference.md)  
  
## <a name="see-also"></a>См. также  
 [Заголовок и сведения о версии SQL Server Express LocalDB](../../relational-databases/express-localdb-instance-apis/sql-server-express-localdb-header-and-version-information.md)  
  
  
