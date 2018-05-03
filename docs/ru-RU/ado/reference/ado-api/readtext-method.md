---
title: Метод ReadText | Документы Microsoft
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Stream::raw_ReadText
- _Stream::ReadText
helpviewer_keywords:
- ReadText method [ADO]
ms.assetid: be5a409e-cf87-4859-9ea5-713401755a77
caps.latest.revision: 16
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 8f211e55e62c4fc2c411a732fa86523ebf572ce1
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="readtext-method"></a>Метод ReadText
Считывает указанное число символов из текстового [поток](../../../ado/reference/ado-api/stream-object-ado.md) объекта.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
String = Stream.ReadText ( NumChars)  
```  
  
#### <a name="parameters"></a>Параметры  
 *NumChars*  
 Необязательно. Объект **длинные** значение, указывающее число символов для чтения из файла или [StreamReadEnum](../../../ado/reference/ado-api/streamreadenum.md) значение. Значение по умолчанию — **adReadAll**.  
  
## <a name="return-value"></a>Возвращаемое значение  
 **ReadText** метод считывает указанное число символов, всю строку или весь поток из **поток** объекта и возвращает результирующую строку.  
  
## <a name="remarks"></a>Замечания  
 Если *NumChar* остается больше числа символов в потоке, возвращаются только символов, оставшихся. Чтение строки заполнено в соответствии с длиной, определяемой *NumChar*. Если нет доступных для чтения символов, возвращается значение типа variant, значение которого равно null. **ReadText** не может использоваться для чтения в обратном направлении.  
  
> [!NOTE]
>  **ReadText** метод используется с текстовыми потоками ([тип](../../../ado/reference/ado-api/type-property-ado-stream.md) — **adTypeText**). Для двоичных потоков (**тип** — **adTypeBinary**), используйте [чтения](../../../ado/reference/ado-api/read-method.md).  
  
 Запросы, которые приводят к большой объем XML-данные возвращенные с помощью **ReadText** Если это делается в компонент COM +, из которой вызывается метод объекта потока объектов данных ActiveX (ADO) может занять немало времени для выполнения; ASP-страницы, сеанс пользователя может истечь время ожидания. ADO преобразует поток объекта данные из кодировки UTF-8 в Юникоде. перераспределение часто памяти, участвующие в преобразовании такой большой объем данных за один раз — довольно много времени. Чтобы решить, выполнять повторяющиеся вызовы к **ReadText** метод ADO объект команды и укажите меньшее число символов. Тесты показали, значение которого эквивалентно значению 128 КБ (131,072) является оптимальной. Время отклика уменьшается, как уменьшить это значение. Дополнительные сведения см. в статье базы знаний 280067, «PRB: получения очень больших XML-документов из SQL Server 2000 с помощью метода ReadText объекта ADO потока может быть медленным», в базе знаний Майкрософт на http://support.microsoft.com.  
  
## <a name="applies-to"></a>Объект применения  
 [Объект Stream (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)  
  
## <a name="see-also"></a>См. также  
 [Метод Read](../../../ado/reference/ado-api/read-method.md)
