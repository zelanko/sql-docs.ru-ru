---
description: MemberTypeEnum
title: Мембертипинум | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- MemberTypeEnum
helpviewer_keywords:
- MemberTypeEnum enumeration [ADO MD]
ms.assetid: 5d8132c0-7ca2-4f86-8336-1b34213869ad
author: rothja
ms.author: jroth
ms.openlocfilehash: 441430cd164be017779afc54ba9af866edaea874
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2020
ms.locfileid: "88986265"
---
# <a name="membertypeenum"></a>MemberTypeEnum
Задает параметр для свойства [Type](./type-property-ado-md.md) объекта- [члена](./member-object-ado-md.md) .  
  
|Константа|Значение|Описание|  
|--------------|-----------|-----------------|  
|**adMemberAll**|4|Указывает, что объект **member** представляет все элементы уровня.|  
|**adMemberFormula**|3|Указывает, что объект- **член** вычисляется с помощью выражения формулы.|  
|**adMemberMeasure**|2|Указывает, что объект- **член** принадлежит измерению Measures и представляет количественный атрибут.|  
|**adMemberRegular**|1|По умолчанию. Указывает, что объект **member** представляет экземпляр бизнес-сущности.|  
|**adMemberUnknown**|0|Не удается определить тип элемента.|