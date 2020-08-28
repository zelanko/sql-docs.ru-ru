---
description: Метод Clone (ADO)
title: Метод Clone (ADO) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset20::Clone
- Recordset20::raw_Clone
helpviewer_keywords:
- Clone method [ADO]
ms.assetid: ad49265f-1c05-4271-9bbf-7c00010ac18c
author: rothja
ms.author: jroth
ms.openlocfilehash: cc7bab8106ba0d9b023999f80ce77935ae30cc8d
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2020
ms.locfileid: "88975435"
---
# <a name="clone-method-ado"></a>Метод Clone (ADO)
Создает дубликат объекта [набора записей](./recordset-object-ado.md) из существующего объекта **набора записей** . При необходимости указывает, что клон доступен только для чтения.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Set rstDuplicate = rstOriginal.Clone (LockType)  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает ссылку на объект **набора записей** .  
  
#### <a name="parameters"></a>Параметры  
 *рстдупликате*  
 Объектная переменная, идентифицирующая дубликат создаваемого объекта **набора записей** .  
  
 *rstOriginal*  
 Объектная переменная, определяющая объект **набора записей** для дублирования.  
  
 *LockType*  
 Необязательный элемент. Значение [локктипинум](./locktypeenum.md) , указывающее либо тип блокировки исходного **набора записей**, либо **набор записей**только для чтения. Допустимые значения: **адлоккунспеЦифиед** или **адлоккреадонли**.  
  
## <a name="remarks"></a>Remarks  
 Используйте метод **clone** для создания нескольких повторяющихся объектов **набора записей** , особенно если требуется поддерживать более одной текущей записи в заданном наборе записей. Использование метода **clone** является более эффективным, чем создание и открытие нового объекта **набора записей** , который использует то же определение, что и исходный.  
  
 Свойство [Filter](./filter-property.md) исходного **набора записей**, если таковое имеется, не будет применено к клону. Задайте свойство **Filter** для нового **набора записей** , чтобы отфильтровать результаты. Самый простой способ скопировать любое существующее значение **фильтра** — это назначить его напрямую, как показано ниже.  
  
```  
rsNew.Filter = rsOriginal.Filter  
```  
  
 Текущей записи только что созданного клона присваивается первая запись.  
  
 Изменения, вносимые в один объект **набора записей** , отображаются во всех его клонах независимо от типа курсора. Однако после выполнения инструкции [Requery](./requery-method.md) для исходного **набора записей**клоны больше не будут синхронизироваться с исходным.  
  
 Закрытие исходного **набора записей** не приводит к закрытию его копий, а копирование не приводит к закрытию оригинала и других копий.  
  
 Можно клонировать только объект **набора записей** , который поддерживает закладки. Значения закладок взаимозаменяемы; то есть ссылка на закладку из одного объекта **Recordset** ссылается на одну и ту же запись в любом из его клонов.  
  
 Некоторые события **набора записей** , которые вызываются, также будут выполняться во всех клонах **набора записей** . Однако поскольку текущая запись может отличаться между клонированными **наборами записей**, события могут быть недопустимыми для клона. Например, при изменении значения поля в измененном **наборе записей** и во всех клонах будет возникать событие [виллчанжефиелд](./willchangefield-and-fieldchangecomplete-events-ado.md) . Параметр *Fields* события **Виллчанжефиелд** клонированного **набора записей** (где изменение не было внесено) будет ссылаться на поля текущей записи клона, что может отличаться от текущей записи исходного **набора записей** , где произошло изменение.  
  
 В следующей таблице приведен полный список всех событий **набора записей** . Указывает, являются ли они допустимыми и запускаются для всех клонов набора записей, созданных с помощью метода **clone** .  
  
|Событие|Активировано в клонах?|  
|-----------|--------------------------|  
|[ендофрекордсет](./endofrecordset-event-ado.md)|Нет|  
|[FetchComplete](./fetchcomplete-event-ado.md)|Нет|  
|[фетчпрогресс](./fetchprogress-event-ado.md)|Нет|  
|[FieldChangeComplete](./willchangefield-and-fieldchangecomplete-events-ado.md)|Да|  
|[мовекомплете](./willmove-and-movecomplete-events-ado.md)|Нет|  
|[RecordChangeComplete](./willchangerecord-and-recordchangecomplete-events-ado.md)|Да|  
|[RecordsetChangeComplete](./willchangerecordset-and-recordsetchangecomplete-events-ado.md)|Нет|  
|[WillChangeField](./willchangefield-and-fieldchangecomplete-events-ado.md)|Да|  
|[WillChangeRecord](./willchangerecord-and-recordchangecomplete-events-ado.md)|Да|  
|[WillChangeRecordset](./willchangerecordset-and-recordsetchangecomplete-events-ado.md)|Нет|  
|[WillMove](./willmove-and-movecomplete-events-ado.md)|Нет|  
  
## <a name="applies-to"></a>Применение  
 [Объект Recordset (ADO)](./recordset-object-ado.md)  
  
## <a name="see-also"></a>См. также  
 [Пример метода Clone (Visual Basic)](./clone-method-example-vb.md)   
 [Пример метода Clone (VBScript)](./clone-method-example-vbscript.md)   
 [Пример метода Clone (Visual C++)](./clone-method-example-vc.md)