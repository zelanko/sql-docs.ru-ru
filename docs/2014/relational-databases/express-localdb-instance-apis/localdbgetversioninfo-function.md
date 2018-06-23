---
title: Функция Localdbgetversionsinfo | Документы Microsoft
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- LocalDBGetVersionInfo
api_location:
- sqluserinstance.dll
topic_type:
- apiref
ms.assetid: d4aaea30-1d0d-4436-bcdc-5c101d27b1c1
caps.latest.revision: 10
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 03e8e4a07dfed1dc2430f020ad221bfb494eb41f
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36192890"
---
# <a name="localdbgetversioninfo-function"></a>Функция LocalDBGetVersionsInfo
  Возвращает сведения для указанной версии SQL Server Express LocalDB — факт ее существования и полный номер версии LocalDB (включая номер сборки и номер выпуска).  
  
 Сведения возвращаются в виде `struct` с именем **LocalDBVersionInfo**, который имеет следующее определение.  
  
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
  
 [LOCALDB_ERROR_NOT_INSTALLED](../express-localdb-error-messages/localdb-error-not-installed.md)  
 Компонент SQL Server Express LocalDB не установлен на компьютере.  
  
 [LOCALDB_ERROR_INVALID_PARAMETER](../express-localdb-error-messages/localdb-error-invalid-parameter.md)  
 Один или несколько указанных входных параметров недопустимы.  
  
 [LOCALDB_ERROR_UNKNOWN_VERSION](../express-localdb-error-messages/localdb-error-unknown-version.md)  
 Указанная версия LocalDB не существует.  
  
 [LOCALDB_ERROR_INTERNAL_ERROR](../express-localdb-error-messages/localdb-error-internal-error.md)  
 Произошла непредвиденная ошибка. Подробные сведения см. в журнале событий.  
  
## <a name="details"></a>Сведения  
 Обоснование появлением `struct` аргумент размера (*lpVersionInfoSize*) — научить API для возврата разных версий **LocalDBVersionInfostruct**, эффективно Включение прямой и обратной совместимости.  
  
 Если `struct` аргумент размера (*lpVersionInfoSize*) соответствует размеру известной версии **LocalDBVersionInfostruct**, соответствующей версии `struct` возвращается. В противном случае возвращается значение LOCALDB_ERROR_INVALID_PARAMETER.  
  
 Типичным примером **LocalDBGetVersionInfo** использование API выглядит следующим образом:  
  
```  
LocalDBVersionInfo vi;  
LocalDBVersionInfo(L”11.0”, &vi, sizeof(LocalDBVersionInfo));  
  
```  
  
## <a name="remarks"></a>Примечания  
 Образец кода, использующего API LocalDB, см. в разделе [SQL Server Express LocalDB Reference](../sql-server-express-localdb-reference.md)  
  
## <a name="see-also"></a>См. также  
 [Заголовок и сведения о версии SQL Server Express LocalDB](sql-server-express-localdb-header-and-version-information.md)  
  
  