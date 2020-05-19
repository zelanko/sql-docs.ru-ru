---
title: ReadText, метод | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Stream::raw_ReadText
- _Stream::ReadText
helpviewer_keywords:
- ReadText method [ADO]
ms.assetid: be5a409e-cf87-4859-9ea5-713401755a77
author: rothja
ms.author: jroth
ms.openlocfilehash: 8afabd90ee6251be650036b285de0f08a3776723
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2020
ms.locfileid: "82754236"
---
# <a name="readtext-method"></a>Метод ReadText
Считывает указанное количество символов из объекта текстового [потока](../../../ado/reference/ado-api/stream-object-ado.md) .  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
String = Stream.ReadText ( NumChars)  
```  
  
#### <a name="parameters"></a>Параметры  
 *NumChars*  
 Необязательный элемент. Значение **типа Long** , указывающее количество символов, считываемых из файла, или значение [стреамреаденум](../../../ado/reference/ado-api/streamreadenum.md) . Значение по умолчанию — **адреадалл**.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод **ReadText** считывает указанное число символов, целую строку или весь поток из объекта **потока** и возвращает результирующую строку.  
  
## <a name="remarks"></a>Remarks  
 Если *нумчар* больше, чем количество символов, оставшихся в потоке, возвращаются только оставшиеся символы. Чтение строки не дополняется в соответствии с длиной, заданной параметром *нумчар*. Если не осталось ни одного символа для чтения, возвращается Variant со значением NULL. **ReadText** нельзя использовать для чтения в обратном направлении.  
  
> [!NOTE]
>  Метод **ReadText** используется с потоками текста ([Type](../../../ado/reference/ado-api/type-property-ado-stream.md) — **адтипетекст**). Для двоичных потоков (**Type** — **Адтипебинари**) используйте [Read](../../../ado/reference/ado-api/read-method.md).  
  
 Запросы, которые приводят к большому количеству XML-данных, возвращаемых через метод **ReadText** объекта потока данных ACTIVEX (ADO), могут занимать много времени. Если это делается в компоненте COM+, который вызывается из страницы ASP, время ожидания сеанса пользователя может истекает. ADO преобразует данные объекта потока из кодировки UTF-8 в Юникод; частое перераспределение памяти, участвующее в преобразовании такого большого количества данных за один раз, занимает много времени. Чтобы устранить эту проблему, выполните повторные вызовы метода **ReadText** объекта команды ADO и укажите меньшее количество символов. Тесты показали, что значение, эквивалентное 128 KБ (131 072), является оптимальным. Время отклика уменьшается, так как это значение уменьшается. Дополнительные сведения см. в статье базы знаний 280067, "PRB. получение очень больших XML-документов из SQL Server 2000 с помощью метода ReadText объекта потока ADO может быть медленнее", в базе знаний Майкрософт по адресу https://support.microsoft.com .  
  
## <a name="applies-to"></a>Применяется к  
 [Объект Stream (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)  
  
## <a name="see-also"></a>См. также  
 [Метод Read](../../../ado/reference/ado-api/read-method.md)
