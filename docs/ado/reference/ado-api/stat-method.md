---
title: "Метод stat | Документы Microsoft"
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- _Stream::Stat
helpviewer_keywords:
- Stat method [ADO]
ms.assetid: 99a2b2d4-e6b1-4205-b011-72d024ea7240
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: c19b5bed54d4bbb27a5aeb235b0e4ab529b9c836
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="stat-method"></a>Stat-метод
Извлекает сведения о [поток](../../../ado/reference/ado-api/stream-object-ado.md) объекта.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Long stream.Stat(StatStg, StatFlag)  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект **длинные** значение, указывающее состояние операции.  
  
#### <a name="parameters"></a>Параметры  
 *StatStg*  
 Структура STATSTG, будут заполнены сведения о потоке. Реализация **Stat** метод, используемый для объекта ADO потока не заполнять все поля структуры.  
  
 *StatFlag*  
 Указывает, что этот метод не возвращает некоторые члены в структуре STATSTG, тем самым экономя операции выделения памяти. Значения берутся из перечисления STATFLAG. Перечисление STATFLAG имеет два значения  
  
|Константа|Значение|  
|--------------|-----------|  
|STATFLAG_DEFAULT|0|  
|STATFLAG_NONAME|1|  
  
## <a name="remarks"></a>Замечания  
 Версия Stat метода, реализованного в объекте ADO Stream заполняет структуры STATSTG следующие поля:  
  
 *pwcsName*  
 Строка, содержащая имя потока, если он доступен и значение StatFlag STATFLAG_NONAME не указан.  
  
 *cbSize*  
 Указывает размер в байтах потока или массива байтов.  
  
 *mtime*  
 Указывает время последнего изменения для этого хранилища, потока или массива байтов.  
  
 *CTime*  
 Указывает время создания для этого хранилища, потока или массива байтов.  
  
 *atime*  
 Указывает время последнего доступа для этого хранилища, потока или массива байтов.  
  
 Если в параметре StatFlag STATFLAG_NONAME, имя потока не возвращается.  
  
 Если STATFLAG_NONAME не указан в параметре StatFlag отсутствует имя для текущего потока, это значение будет E_NOTIMPL.  
  
## <a name="applies-to"></a>Объект применения  
 [Объект потока (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)

