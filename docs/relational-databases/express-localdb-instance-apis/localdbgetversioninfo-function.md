---
title: Функция Localdbgetversionsinfo | Документация Майкрософт
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
apiname:
- LocalDBGetVersionInfo
apilocation:
- sqluserinstance.dll
apitype: DLLExport
ms.assetid: d4aaea30-1d0d-4436-bcdc-5c101d27b1c1
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: d45c83b0a8c7ce0884809c394ea35d21dbc42c75
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "62639787"
---
# <a name="localdbgetversioninfo-function"></a>Функция LocalDBGetVersionsInfo
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Возвращает сведения для указанной версии SQL Server Express LocalDB — факт ее существования и полный номер версии LocalDB (включая номер сборки и номер выпуска).  
  
 Сведения возвращаются в виде **структуры** с именем **LocalDBVersionInfo**, который имеет следующее определение.  
  
```  
typedef struct _LocalDBVersionInfo  
{  
      // Contains the size of the LocalDBVersionInfo struct  
      DWORD  cbLocalDBVersionInfoSize;  
  
      // Holds the version name  
      TLocalDBVersionwszVersion;  
  
      // TRUE if the instance files exist on disk, FALSE otherwise  
      BOOL   bExists;  
  
      // Holds the LocalDB version for the instance in the format: major.minor.build.revision  
      DWORD  dwMajor;  
      DWORD  dwMinor;  
      DWORD  dwBuild;  
      DWORD  dwRevision;  
} LocalDBVersionInfo;  
  
```  
  
 **Файл заголовка:** sqlncli.h  
  
## <a name="syntax"></a>Синтаксис  
  
```  
HRESULT LocalDBGetVersionInfo(  
           PCWSTR wszVersionName,           PLocalDBVersionInfo pVersionInfo,           DWORD dwVersionInfoSize);  
```  
  
## <a name="parameters"></a>Параметры  
 *wszVersionName*  
 [Вход] Имя версии LocalDB.  
  
 *pVersionInfo*  
 [Выход] Буфер для хранения сведений о версии LocalDB.  
  
 *dwVersionInfoSize*  
 [Вход] Содержит размер *VersionInfo* буфера.  
  
## <a name="returns"></a>Возвращает  
 S_OK  
 Функция выполнена успешно.  
  
 [LOCALDB_ERROR_NOT_INSTALLED](../../relational-databases/express-localdb-error-messages/localdb-error-not-installed.md)  
 Компонент SQL Server Express LocalDB не установлен на компьютере.  
  
 [LOCALDB_ERROR_INVALID_PARAMETER](../../relational-databases/express-localdb-error-messages/localdb-error-invalid-parameter.md)  
 Один или несколько указанных входных параметров недопустимы.  
  
 [LOCALDB_ERROR_UNKNOWN_VERSION](../../relational-databases/express-localdb-error-messages/localdb-error-unknown-version.md)  
 Указанная версия LocalDB не существует.  
  
 [LOCALDB_ERROR_INTERNAL_ERROR](../../relational-databases/express-localdb-error-messages/localdb-error-internal-error.md)  
 Произошла непредвиденная ошибка. Подробные сведения см. в журнале событий.  
  
## <a name="details"></a>Сведения  
 Обоснование появлением **структуры** аргумент размера (*lpVersionInfoSize*) является возможность API мог возвращать различные версии структуры **LocalDBVersionInfostruct**, что включение прямой и обратной совместимости.  
  
 Если **структуры** аргумент размера (*lpVersionInfoSize*) соответствует размеру известной версии **LocalDBVersionInfostruct**, эту версию  **Структура** возвращается. В противном случае возвращается значение LOCALDB_ERROR_INVALID_PARAMETER.  
  
 Типичным примером **LocalDBGetVersionInfo** использование API выглядит следующим образом:  
  
```  
LocalDBVersionInfo vi;  
LocalDBVersionInfo(L"11.0", &vi, sizeof(LocalDBVersionInfo));  
  
```  
  
## <a name="remarks"></a>Примечания  
 Образец кода, использующего API LocalDB, см. в разделе [SQL Server Express LocalDB Reference](../../relational-databases/sql-server-express-localdb-reference.md)  
  
## <a name="see-also"></a>См. также  
 [Заголовок и сведения о версии SQL Server Express LocalDB](../../relational-databases/express-localdb-instance-apis/sql-server-express-localdb-header-and-version-information.md)  
  
  
