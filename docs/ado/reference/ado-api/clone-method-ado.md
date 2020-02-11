---
title: Метод Clone (ADO) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 7439f9a4a04582f4cf4c4878892ed0f4f33e228c
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "67920019"
---
# <a name="clone-method-ado"></a>Метод Clone (ADO)
Создает дубликат объекта [набора записей](../../../ado/reference/ado-api/recordset-object-ado.md) из существующего объекта **набора записей** . При необходимости указывает, что клон доступен только для чтения.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Set rstDuplicate = rstOriginal.Clone (LockType)  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает ссылку на объект **набора записей** .  
  
#### <a name="parameters"></a>Параметры  
 *рстдупликате*  
 Объектная переменная, идентифицирующая дубликат создаваемого объекта **набора записей** .  
  
 *рсторигинал*  
 Объектная переменная, определяющая объект **набора записей** для дублирования.  
  
 *LockType*  
 Необязательный параметр. Значение [локктипинум](../../../ado/reference/ado-api/locktypeenum.md) , указывающее либо тип блокировки исходного **набора записей**, либо **набор записей**только для чтения. Допустимые значения: **адлоккунспеЦифиед** или **адлоккреадонли**.  
  
## <a name="remarks"></a>Remarks  
 Используйте метод **clone** для создания нескольких повторяющихся объектов **набора записей** , особенно если требуется поддерживать более одной текущей записи в заданном наборе записей. Использование метода **clone** является более эффективным, чем создание и открытие нового объекта **набора записей** , который использует то же определение, что и исходный.  
  
 Свойство [Filter](../../../ado/reference/ado-api/filter-property.md) исходного **набора записей**, если таковое имеется, не будет применено к клону. Задайте свойство **Filter** для нового **набора записей** , чтобы отфильтровать результаты. Самый простой способ скопировать любое существующее значение **фильтра** — это назначить его напрямую, как показано ниже.  
  
```  
rsNew.Filter = rsOriginal.Filter  
```  
  
 Текущей записи только что созданного клона присваивается первая запись.  
  
 Изменения, вносимые в один объект **набора записей** , отображаются во всех его клонах независимо от типа курсора. Однако после выполнения инструкции [Requery](../../../ado/reference/ado-api/requery-method.md) для исходного **набора записей**клоны больше не будут синхронизироваться с исходным.  
  
 Закрытие исходного **набора записей** не приводит к закрытию его копий, а копирование не приводит к закрытию оригинала и других копий.  
  
 Можно клонировать только объект **набора записей** , который поддерживает закладки. Значения закладок взаимозаменяемы; то есть ссылка на закладку из одного объекта **Recordset** ссылается на одну и ту же запись в любом из его клонов.  
  
 Некоторые события **набора записей** , которые вызываются, также будут выполняться во всех клонах **набора записей** . Однако поскольку текущая запись может отличаться между клонированными **наборами записей**, события могут быть недопустимыми для клона. Например, при изменении значения поля в измененном **наборе записей** и во всех клонах будет возникать событие [виллчанжефиелд](../../../ado/reference/ado-api/willchangefield-and-fieldchangecomplete-events-ado.md) . Параметр *Fields* события **Виллчанжефиелд** клонированного **набора записей** (где изменение не было внесено) будет ссылаться на поля текущей записи клона, что может отличаться от текущей записи исходного **набора записей** , где произошло изменение.  
  
 В следующей таблице приведен полный список всех событий **набора записей** . Указывает, являются ли они допустимыми и запускаются для всех клонов набора записей, созданных с помощью метода **clone** .  
  
|Событие|Активировано в клонах?|  
|-----------|--------------------------|  
|[ендофрекордсет](../../../ado/reference/ado-api/endofrecordset-event-ado.md)|нет|  
|[фетчкомплете](../../../ado/reference/ado-api/fetchcomplete-event-ado.md)|нет|  
|[фетчпрогресс](../../../ado/reference/ado-api/fetchprogress-event-ado.md)|нет|  
|[фиелдчанжекомплете](../../../ado/reference/ado-api/willchangefield-and-fieldchangecomplete-events-ado.md)|Да|  
|[мовекомплете](../../../ado/reference/ado-api/willmove-and-movecomplete-events-ado.md)|нет|  
|[рекордчанжекомплете](../../../ado/reference/ado-api/willchangerecord-and-recordchangecomplete-events-ado.md)|Да|  
|[рекордсетчанжекомплете](../../../ado/reference/ado-api/willchangerecordset-and-recordsetchangecomplete-events-ado.md)|нет|  
|[виллчанжефиелд](../../../ado/reference/ado-api/willchangefield-and-fieldchangecomplete-events-ado.md)|Да|  
|[виллчанжерекорд](../../../ado/reference/ado-api/willchangerecord-and-recordchangecomplete-events-ado.md)|Да|  
|[виллчанжерекордсет](../../../ado/reference/ado-api/willchangerecordset-and-recordsetchangecomplete-events-ado.md)|нет|  
|[виллмове](../../../ado/reference/ado-api/willmove-and-movecomplete-events-ado.md)|нет|  
  
## <a name="applies-to"></a>Применяется к  
 [Объект Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>См. также:  
 [Пример метода Clone (Visual Basic)](../../../ado/reference/ado-api/clone-method-example-vb.md)   
 [Пример метода Clone (VBScript)](../../../ado/reference/ado-api/clone-method-example-vbscript.md)   
 [Пример метода Clone (Visual C++)](../../../ado/reference/ado-api/clone-method-example-vc.md)   
