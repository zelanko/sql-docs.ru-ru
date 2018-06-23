---
title: Функция LocalDBStartTracing | Документы Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- LocalDBStartTracing
api_location:
- sqluserinstance.dll
topic_type:
- apiref
ms.assetid: c7b83833-6d2a-4a06-9cb7-42767bed52c6
caps.latest.revision: 10
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: e54d3381fcec5da1d82ce512ead0474ae2c4c82c
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36096862"
---
# <a name="localdbstarttracing-function"></a>Функция LocalDBStartTracing
  Включает трассировку вызовов API для всех экземпляров SQL Server Express LocalDB, принадлежащих текущему пользователю Windows.  
  
 **Файл заголовка:** sqlncli.h  
  
## <a name="syntax"></a>Синтаксис  
  
```  
HRESULT LocalDBStartTracing();  
```  
  
## <a name="returns"></a>Возвращает  
 S_OK  
 Функция выполнена успешно.  
  
 [LOCALDB_ERROR_XEVENT_FAILED](../express-localdb-error-messages/localdb-error-xevent-failed.md)  
 Не удалось запустить подсистему XEvent в API экземпляра LocalDB.  
  
 [LOCALDB_ERROR_INTERNAL_ERROR](../express-localdb-error-messages/localdb-error-internal-error.md)  
 Произошла непредвиденная ошибка. Подробные сведения см. в журнале событий.  
  
## <a name="remarks"></a>Примечания  
 Образец кода, использующего API LocalDB, см. в разделе [SQL Server Express LocalDB Reference](../sql-server-express-localdb-reference.md)  
  
## <a name="see-also"></a>См. также  
 [Заголовок и сведения о версии SQL Server Express LocalDB](sql-server-express-localdb-header-and-version-information.md)  
  
  