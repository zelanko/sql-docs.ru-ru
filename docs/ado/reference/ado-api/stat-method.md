---
title: Stat, метод | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Stream::Stat
helpviewer_keywords:
- Stat method [ADO]
ms.assetid: 99a2b2d4-e6b1-4205-b011-72d024ea7240
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 0538a3afae1e4c0bf4159d8ef6a42872f21ff6ed
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "67916873"
---
# <a name="stat-method"></a>Метод Stat
Извлекает сведения об объекте [потока](../../../ado/reference/ado-api/stream-object-ado.md) .  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Long stream.Stat(StatStg, StatFlag)  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Значение **типа Long** , указывающее состояние операции.  
  
#### <a name="parameters"></a>Параметры  
 *статстг*  
 Структура СТАТСТГ, которая будет заполнена сведениями о потоке. Реализация метода **stat** , используемого объектом потока ADO, не заполняет все поля структуры.  
  
 *статфлаг*  
 Указывает, что этот метод не возвращает некоторые члены структуры СТАТСТГ, тем самым сохраняя операцию выделения памяти. Значения берутся из перечисления СТАТФЛАГ. Перечисление СТАТФЛАГ имеет два значения  
  
|Постоянно|Значение|  
|--------------|-----------|  
|STATFLAG_DEFAULT|0|  
|STATFLAG_NONAME|1|  
  
## <a name="remarks"></a>Remarks  
 Версия метода Stat, реализованного для объекта потока ADO, заполняет следующие поля структуры СТАТСТГ:  
  
 *пвкснаме*  
 Строка, содержащая имя потока, если такой объект доступен, а значение Статфлаг STATFLAG_NONAME не указано.  
  
 *кбсизе*  
 Задает размер в байтах потока или массива байтов.  
  
 *мтиме*  
 Указывает время последнего изменения для этого хранилища, потока или массива байтов.  
  
 *CTime*  
 Указывает время создания для этого хранилища, потока или массива байтов.  
  
 *времени atime*  
 Указывает время последнего доступа для этого хранилища, потока или массива байтов.  
  
 Если в параметре Статфлаг указано значение STATFLAG_NONAME, то имя потока не возвращается.  
  
 Если STATFLAG_NONAME не было указано в параметре Статфлаг и для текущего потока нет доступных имен, это значение будет E_NOTIMPL.  
  
## <a name="applies-to"></a>Применяется к  
 [Объект Stream (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)
