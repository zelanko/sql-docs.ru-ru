---
title: Функция Localdbgetversionsinfo | Документация Майкрософт
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
api_name:
- LocalDBGetVersionInfo
api_location:
- sqluserinstance.dll
topic_type:
- apiref
ms.assetid: d4aaea30-1d0d-4436-bcdc-5c101d27b1c1
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: cce316685bccb2724eb89965e4e466fe58fb807e
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/18/2020
ms.locfileid: "85027727"
---
# <a name="localdbgetversioninfo-function"></a>Функция LocalDBGetVersionsInfo
  Возвращает сведения для указанной версии SQL Server Express LocalDB — факт ее существования и полный номер версии LocalDB (включая номер сборки и номер выпуска).  
  
 Эти сведения возвращаются в виде `struct` именованной **локалдбверсионинфо**, которая имеет следующее определение.  
  
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
 *всзверсионнаме*  
 [Вход] Имя версии LocalDB.  
  
 *пверсионинфо*  
 [Выход] Буфер для хранения сведений о версии LocalDB.  
  
 *двверсионинфосизе*  
 Входной Содержит размер буфера *versionInfo* .  
  
## <a name="returns"></a>Возвращаемое значение  
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
 Смысл в поведении `struct` аргумента size (*лпверсионинфосизе*) заключается в том, чтобы позволить API возвращать различные версии **локалдбверсионинфострукт**, эффективно обеспечивая прямую и обратную совместимость.  
  
 Если `struct` аргумент size (*лпверсионинфосизе*) соответствует размеру известной версии **локалдбверсионинфострукт**, возвращается эта версия `struct` . В противном случае возвращается значение LOCALDB_ERROR_INVALID_PARAMETER.  
  
 Типичный пример использования API **localdbgetversionsinfo** выглядит следующим образом:  
  
```  
LocalDBVersionInfo vi;  
LocalDBVersionInfo(L"11.0", &vi, sizeof(LocalDBVersionInfo));  
  
```  
  
## <a name="remarks"></a>Remarks  
 Образец кода, использующего API LocalDB, см. в разделе [SQL Server Express LocalDB Reference](../sql-server-express-localdb-reference.md)  
  
## <a name="see-also"></a>См. также:  
 [Заголовок и сведения о версии SQL Server Express LocalDB](sql-server-express-localdb-header-and-version-information.md)  
  
  
