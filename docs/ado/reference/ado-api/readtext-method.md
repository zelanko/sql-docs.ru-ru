---
title: Метод ReadText | Документация Майкрософт
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: d6c174d2e6a659a3b9da8f89816b5bdf90342416
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67917371"
---
# <a name="readtext-method"></a>Метод ReadText
Чтение указанного количество символов из текстового [Stream](../../../ado/reference/ado-api/stream-object-ado.md) объекта.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
String = Stream.ReadText ( NumChars)  
```  
  
#### <a name="parameters"></a>Параметры  
 *число символов*  
 Необязательный параметр. Объект **Long** значение, указывающее количество символов для чтения из файла, или [StreamReadEnum](../../../ado/reference/ado-api/streamreadenum.md) значение. Значение по умолчанию — **adReadAll**.  
  
## <a name="return-value"></a>Возвращаемое значение  
 **ReadText** метод считывает указанное число символов, всю строку или весь поток, из **Stream** объекта и возвращает результирующую строку.  
  
## <a name="remarks"></a>Примечания  
 Если *NumChar* остается больше, чем количество символов в потоке, возвращаются только осталось символов. Чтение строки заполнено в соответствии с длиной, определяемой *NumChar*. Если нет символов, доступных для чтения, возвращается значение variant, значение которого равно null. **ReadText** не может использоваться для чтения в обратном направлении.  
  
> [!NOTE]
>  **ReadText** метод используется с текстовыми потоками ([тип](../../../ado/reference/ado-api/type-property-ado-stream.md) — **adTypeText**). Для двоичных потоков (**тип** — **adTypeBinary**), используйте [чтения](../../../ado/reference/ado-api/read-method.md).  
  
 Запросы, которые приводят к большой объем данных XML, возвращаемых через **ReadText** Если это делается в компоненте COM +, из которой вызывается метод объекта Stream объектов данных ActiveX (ADO) может занять немало времени для выполнения; ASP-странице, сеанс пользователя может истечь время ожидания. ADO преобразует данные объекта Stream из кодировки UTF-8 в Юникод; перераспределение часто памяти, участвующие в преобразовании такое большое количество данных за один раз — довольно много времени. Чтобы решить, выполнять повторные вызовы **ReadText** метод ADO команды объекта и укажите меньшее число символов. Тесты показали, что равно 128 КБ (131,072) является оптимальным. Время отклика уменьшается, как уменьшить это значение. Дополнительные сведения см. в статье базы знаний 280067, «PRB: Получение очень больших XML-документов из SQL Server 2000 с помощью метода ReadText объект stream ADO может падать», в базе знаний Майкрософт в https://support.microsoft.com.  
  
## <a name="applies-to"></a>Объект применения  
 [Объект Stream (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)  
  
## <a name="see-also"></a>См. также  
 [Метод Read](../../../ado/reference/ado-api/read-method.md)
